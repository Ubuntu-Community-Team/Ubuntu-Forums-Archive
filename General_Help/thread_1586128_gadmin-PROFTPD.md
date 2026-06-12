---
title: "gadmin-PROFTPD"
date: 2010-10-01
forum: General Help
---

### Post by PBComputer on 2010-10-01
hello

i'm running Ubuntu 10.4 Lucid Lynx and im setting up gadmin-PROFTPD and when i try and activate it i get the following message and am really unsure where to go from here

 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 56 of '/etc/proftpd/proftpd.conf'

Paul

---

### Post by jwferk on 2010-11-02
same problem here.

---

### Post by jwferk on 2010-11-02
open gadmin-proftpd via the terminal or using ALT+F2

Select the "Server" tab

Scroll to the bottom of the page and find the line

"Generate new certificate"  Hit the "Apply" button to generate the new certificate.

if you are using a terminal you will get this output:

writing new private key to 'cakey.pem'
-----
Generating a 1024 bit RSA private key
.................++++++
................++++++
writing new private key to 'key.pem'
-----
Using configuration from /etc/gadmin-proftpd/certs/gadmin-proftpd-openssl.conf
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
organizationName      :PRINTABLE:'somename'
localityName          :PRINTABLE:'someplace
stateOrProvinceName   :PRINTABLE:'US'
countryName           :PRINTABLE:'EN'
commonName            :PRINTABLE:'localhost'
Certificate is to be certified until Bad time value (999999 days)

Write out database with 1 new entries
Data Base Updated

---

