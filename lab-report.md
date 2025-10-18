# DVWA Lab Report
- **Objective:** Extract user data by exploiting unsanitized SQL queries.
- **Low-level payload:** `' OR '1'='1' --`
- **Steps:** Access SQLi page, submit payload, capture response via Burp Suite.
- **Evidence:** Screenshot of returned table, intercepted HTTP requests.
- **Mitigation:** Use prepared statements and validate inputs.


### Reflected XSS
- **Objective:** Execute client-side scripts via user input.
- **Payloads:** `<script>alert('XSS')</script>`, `"><img src=x onerror=alert(1)>`
- **Steps:** Inject payload into input/search fields, observe alerts.
- **Mitigation:** Contextual output encoding, CSP, HTTP-only cookies.


### Stored XSS
- **Objective:** Store malicious scripts in server-side data and trigger on retrieval.
- **Steps:** Post payloads in forms that save data, observe alerts on page load.
- **Mitigation:** Sanitize stored data, encode output.


### Command Injection
- **Objective:** Execute OS commands via vulnerable input fields.
- **Payloads:** `127.0.0.1; whoami`, `; cat /etc/passwd`
- **Mitigation:** Avoid passing user input to shell commands; whitelist inputs.


### File Inclusion (LFI/RFI)
- **Objective:** Include local or remote files through vulnerable parameters.
- **Payloads:** `../../../../etc/passwd`
- **Mitigation:** Use allowlists, disable remote include, sanitize inputs.


### CSRF & Broken Authentication
- **Objective:** Demonstrate CSRF form and session handling vulnerabilities.
- **Mitigation:** Use CSRF tokens, SameSite cookies, secure session management.


## 3 — Evidence Collection
- Screenshots for each exploit step.
- Intercepted HTTP requests/responses.
- Notes describing why payloads worked.


## 4 — Mitigation & Fixes
- Parameterized queries for SQL.
- Contextual output encoding and CSP.
- Secure cookie flags and session expiration.
- Avoid shell commands with unsanitized input.
- Harden PHP configuration: disable `allow_url_include`, set `open_basedir`.


## 5 — Appendix: Payloads & Helper Commands
- SQLi: `' OR '1'='1' --`, `' UNION SELECT NULL, username, password FROM users --`
- XSS: `<script>alert(1)</script>`, `"><img src=x onerror=alert(1)>`
- Command Injection: `127.0.0.1; whoami`
- LFI: `../../../../etc/passwd`
- Helper commands for lab verification.


## 6 — References
- [DVWA Official Repo](https://github.com/digininja/DVWA)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
