---
title: "Https or security problem"
date: 2009-11-22
forum: General Help
---

### Post by nah40 on 2009-11-22
Since upgrading from 9.04 32 bit to 9.10 64 bit i am unable to connect to the following site [Https://theidahobank.com](Https://theidahobank.com)
This failure occurs with four different browsers I have tried.
Firefox or IE works in Windows.
Any ideas on how to resolve this will be greatly appreciated.

---

### Post by masterfishslayer on 2009-11-22
I cant get in either on 9,10

---

### Post by 1Nadie on 2009-11-22
I when to that bank without any problem
W7 opera browser!!

---

### Post by nah40 on 2009-11-22
thanks 1Nadie, i will give Opera a try.

---

### Post by nah40 on 2009-11-22
Opera does not connect to the site.
I guess it is some kind of security problem, and not a browser one.

---

### Post by Slowspeed on 2009-11-22
Your security setting are likely keeping you from accessing a website with a bad or expired security certificate:

Technical Details

          

theidahobank.com uses an invalid security certificate.

The certificate is only valid for [www.theidahobank.com](www.theidahobank.com)

(Error code: ssl_error_bad_cert_domain)

This is what I received from my firefox in karmic. If you are sure this is a valid site you can create an exception.

---

### Post by Scott753 on 2009-11-22
Interesting. When I clicked on your link, Firefox gave me an untrusted security certificate warning.

but when I added a www in front of it, no problems.

Is the ss below the website?

If so, I'm wondering if it's a security certificate issue and you may have to change those settings.

or try this

[https://www.theidahobank.com/](https://www.theidahobank.com/)

and post the results.

While I was writing this, Slowspeed posted with pretty much the same thing. :)

---

### Post by nah40 on 2009-11-23
Firefox gives me the traingle in front of the address stating the security warning, but no option for an exception as in other similar situations.
the firefox page displayed just is the standard cannoct page saying maybe be firewalled, are you connected to the internet, etc.

---

