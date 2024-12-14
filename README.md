# Legacy Cookie Parsing Detection

## Overview

The **Legacy Cookie Parsing Detection** template is designed to detect web servers or frameworks that rely on or support legacy cookie parsing standards. Specifically, it targets those that may default to outdated parsing logic when a `$Version` attribute is present in the cookie header.

This vulnerability can be exploited by attackers to manipulate cookie behavior in legacy systems, potentially leading to security vulnerabilities such as session hijacking, improper access control, and more.

---

## Template Details

### Name: 
Legacy Cookie Parsing Detection

### Author:
s1d6p01nt7

### Severity:
Medium

### Description:
This template is focused on detecting web servers or frameworks that continue to support legacy cookie parsing standards such as RFC2109 and RFC6265. If the cookie header contains the `$Version` attribute, some servers may fall back to outdated parsing mechanisms, potentially leading to unexpected behavior that attackers could exploit.

It is important to ensure that web servers and frameworks follow the most current cookie parsing standards to avoid these potential issues.

### Remediation:
- Ensure that your web server or framework is configured to follow the latest cookie parsing standards (RFC6265).
- Avoid legacy cookie parsing logic by ensuring that no fallback mechanisms to older standards (e.g., RFC2109) are in place.
- Apply any necessary patches or configuration changes from the vendor to ensure adherence to modern standards.

---

## Vulnerability Details

### Vulnerability:
Web servers or frameworks that support legacy cookie parsing standards (RFC2109 and RFC6265) may introduce risks due to outdated parsing logic, particularly when the `$Version` attribute is present in cookies.

When a web server supports legacy parsing logic, it might not properly handle cookies with special attributes such as `$Version`. This behavior could lead to unintended or insecure handling of cookies, allowing attackers to craft cookies in a way that the server misinterprets or improperly processes them.

### Exploitation:
An attacker could craft a malicious cookie with a `$Version` attribute that triggers the server to revert to legacy cookie parsing. This could allow the attacker to manipulate the behavior of the server or bypass security controls.

### Example Exploit:
A possible exploit scenario would be using a specially crafted cookie:

```http
Cookie: $Version=1; TestCookie="foo\072bar"; $Path="/"; $Domain=example.com
