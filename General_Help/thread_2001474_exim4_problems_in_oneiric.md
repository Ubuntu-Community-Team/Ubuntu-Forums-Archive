---
title: "exim4 problems in oneiric"
date: 2012-06-10
forum: General Help
---

### Post by nardis_Miles1 on 2012-06-10
I have installed oneiric on a 32-bit machine that has, in the past, run exim4 easily. I cannot receive any email. My mainlog file is full of errors like:

2012-06-10 08:40:43 H=etrn.swcp.com [216.184.2.71] F=<ubuntu-users-bounces@lists.ubuntu.com> temporarily rejected RCPT <edwardsa@icantbelieveimdoingthis.com>

I ran MXTool on my domain and everything looks good (good Rdns, good dns, etc.)

Any insight would be helpful.

Art Edwards

---

### Post by ikt on 2012-06-10
Looks like grey listing, do you have that as an option anywhere?

---

### Post by nardis_Miles1 on 2012-06-10
I haven't set grey listing anywhere.

---

### Post by ikt on 2012-06-11
Tried taking out your anti-spam rules?

---

### Post by nardis_Miles1 on 2012-06-11
As naive as this sounds, I have no antispam settings in exim4. I deal with that using filtering after pop3.

---

### Post by nardis_Miles1 on 2012-06-11
After I turned off TLS, the mailer worked. Any experience with TLS errors?

---

### Post by ikt on 2012-06-11
> **nardis_Miles1 said:**
> After I turned off TLS, the mailer worked. Any experience with TLS errors?

Interesting, I would have thought if there were TLS issues the emails would be getting rejected outright.

I'm just about to get started into that TLS/SSL SSMTP/mail side of things, but alas at this point in time, it's just a really strange issue to me :/

---

