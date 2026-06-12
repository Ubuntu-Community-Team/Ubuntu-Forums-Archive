---
title: "pem error"
date: 2012-08-07
forum: General Help
---

### Post by qwertyjjj on 2012-08-07
I get a PEM error when trying to create a VPN certificate.
Any ideas what causes this?


>>
>>
> Here is the result...seems to give a db error
>
> [root@uname 2.0]# ./pkitool karine
> Using Common Name: IP.IPP.IPP.IP
> Generating a 1024 bit RSA private key
> ............++++++
> .++++++
> writing new private key to 'karine.key'
> -----
> Using configuration from /etc/openvpn/easy-rsa/2.0/openssl-1.0.0.cnf
> Check that the request matches the signature
> Signature ok
> The Subject's Distinguished Name is as follows
> countryName :PRINTABLE:'FR'
> stateOrProvinceName :PRINTABLE:'FR'
> localityName :PRINTABLE:'Paris'
> organizationName :PRINTABLE:'CompanyNameFR'
> organizationalUnitName:PRINTABLE:'CompanyNameFR'
> commonName :PRINTABLE:'IP.IPP.IPP.IP'
> name :PRINTABLE:'IP.IPP.IPP.IP'
> emailAddress :IA5STRING:'aide@companyname.eu'
> Certificate is to be certified until Aug 3 06:32:28 2022 GMT (3650 days)
> failed to update database
> TXT_DB error number 2
>
>
>
Also, when I have a look at the index.txt file it says there are 3 certificates in there but they are all called unknown.

I am using the pkitool as this runs in a script...so I cannot use the built in openvpn commands and have to use the pkitool.

---

