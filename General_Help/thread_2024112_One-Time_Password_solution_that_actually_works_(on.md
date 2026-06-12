---
title: "One-Time Password solution that actually works (on 12.04)?"
date: 2012-07-13
forum: General Help
---

### Post by gsklee on 2012-07-13
Hi all,

I am looking for some OTP package that actually works for my Ubuntu 12.04, needing it so I can log into office VPN.

There is a "pin number" that is only known to me and my system admin, which I need to enter each time I'm trying to generate an OTP.

I've tried the "otp" package, but can't figure out how to make it work. More specifically I can't figure out how to input the pin number. Anyone got any idea? Or any alternative solutions? Thanks!

---

### Post by gsklee on 2012-07-15
***BUMP***

Would be really surprised if there is no working OTP solution on Linux currently at all...

---

### Post by nowen on 2012-07-16
our two-factor authentication server has .debs for Ubuntu for both our opensource Community or Enterprise editions.  We also have a bunch of how-tos for adding two-factor authentication to servers using pam for SSH.  Please see [http://www.wikidsystems.com](http://www.wikidsystems.com).  Here's doc on pam radius & Ubuntu: [http://www.wikidsystems.com/support/wikid-support-center/how-to/how-to-configure-pam-radius-in-ubuntu?searchterm=pam+ubuntu](http://www.wikidsystems.com/support/wikid-support-center/how-to/how-to-configure-pam-radius-in-ubuntu?searchterm=pam+ubuntu)

HTH,

Nick

---

