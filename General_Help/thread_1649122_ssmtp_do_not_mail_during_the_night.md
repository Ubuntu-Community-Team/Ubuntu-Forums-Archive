---
title: "ssmtp: do not mail during the night"
date: 2010-12-19
forum: General Help
---

### Post by KasperH on 2010-12-19
Hi,

Environment:
Ubuntu 8.04.4 server (no X)
with 192 Mb RAM, 
Situation:
my system sometimes emails me to my mobile, but.... I would like to hold these emails during the night...
I know sendmail(1) is/was able to hold off "expensive" transports during certain hours (never worked with it though), but I do not want to turn this little machine into a full MTA. Right now I use ssmtp(1), relaying through gmail.
questions:
1) Is there a setting for this in ssmtp? I have not discovered it.
2) Is there an alternative that can hold sending email during certain hours, as simple as ssmtp(1) without turning the system into a MTA

I have some experience with sendmail 5.65 and 8.13 (10 - 15 years ago), none with postfix

thnx

---

