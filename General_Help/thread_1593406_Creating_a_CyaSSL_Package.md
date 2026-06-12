---
title: "Creating a CyaSSL Package?"
date: 2010-10-11
forum: General Help
---

### Post by ccflyer on 2010-10-11
Hello,

Does anyone have experience creating packages and rolling them into Ubuntu?  I believe that the CyaSSL Embedded SSL Library would be an excellent addition to the Ubuntu distribution, but have no experience creating packages for Ubuntu.

CyaSSL is a C language based SSL library targeted for embedded and RTOS environments, primarily because of its small size and speed.  CyaSSL is up to 20 times smaller than OpenSSL, and yaSSL is already an Ubuntu Partner.  Features include:

- Support for SSL 3.0, TLS 1.0, 1.1, 1.2
- Minimum size of 30-100kb
- Runtime memory of 5-50kb
- OpenSSL Compatibility Layer
- Support for many ciphers, including RABBIT and HC-128 stream ciphers

For a full feature list, you can view the product page here:  [http://yassl.com/yaSSL/Products_cyassl.html]("http://yassl.com/yaSSL/Products_cyassl.html")

I have created a bug in launchpad for this, which can be found here:
[https://bugs.launchpad.net/ubuntu/+bug/624840]("http://yassl.com/yaSSL/Products_cyassl.html")

If anyone has any suggestions or advice, it would be very much appreciated.

Thanks,
Chris C.

---

