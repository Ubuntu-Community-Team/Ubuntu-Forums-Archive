---
title: "Smtp?"
date: 2009-07-25
forum: General Help
---

### Post by Ramonster on 2009-07-25
Good day,

I got an apache server and mysql server up. But If I try to send my newsletter to my subcribers I can't send anything from my website-newsletter application... will I need to setup a smtp server for this?

Thanks in advance,

-Ramon

---

### Post by Ramonster on 2009-07-26
bump?

---

### Post by DaithiF on 2009-07-26
Hi Ramonster,
short of installing a full mailserver like sendmail or exim4, you can usually send emails via your ISP using SMTP.  There a variety of command line programs that can send smtp mails -- sendEmail is one, ssmtp, msmtp are others.  Install one of these, then check out the smtp settings required for your ISP.

good luck

---

