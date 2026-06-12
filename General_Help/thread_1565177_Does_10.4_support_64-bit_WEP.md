---
title: "Does 10.4 support 64-bit WEP?"
date: 2010-08-31
forum: General Help
---

### Post by Leadfinger on 2010-08-31
I installed 9.10 onto an old Toshiba Portege 4010 laptop.  When it got loaded, I run Software Update to get it up to 10.4.  BUT...even though the system connected to my WiFi just fine in 9.10, it won't connect at all in 10.4

Am I missing something?
(The video driver isn't correct either, but that's another thread....)

---

### Post by Leadfinger on 2010-09-01
Edit:

My basic question is... Does 10.4 not support plain old 64-bit WEP anymore?  (That's the encryption running on my wireless)

---

### Post by LowSky on 2010-09-01
WEP is one of the worst ways to encrypt your connection. you should really use  WPA2

---

### Post by uRock on 2010-09-01
> **LowSky said:**
> WEP is one of the worst ways to encrypt your connection. you should really use  WPA2
+1 WEP is very easily cracked, but if you do not have a choice, then yes Ubuntu does support your needs with WEP.

---

### Post by Leadfinger on 2010-09-01
I'm not worried so much about suport security.  In my experience, WEP is more compatible than WPA.  (except in this case, obviously)

Anyway, I wonder of the issue has less to do with Ubuntu, and more to do with my FiOS connection.  Note that my FiOS router supports 64-bit WEP... Ubuntu only has options for 40 and 128-bit.  I'm guessing that's the soource of the issue.  What do you guys think?

---

### Post by Grenage on 2010-09-01
> **Leadfinger said:**
> I'm not worried so much about suport security.  In my experience, WEP is more compatible than WPA.  (except in this case, obviously)

Anyway, I wonder of the issue has less to do with Ubuntu, and more to do with my FiOS connection.  Note that my FiOS router supports 64-bit WEP... Ubuntu only has options for 40 and 128-bit.  I'm guessing that's the soource of the issue.  What do you guys think?

64 bit WEP is horrendous, it can be cracked in minutes.  For the love of God, use at least WPA - compatibility was an issue 5-6 years ago, but now?

Anyhow, it sounds like you've found the source of the problem.

---

### Post by Leadfinger on 2010-09-02
I actually haven't found the source yet.  I've changed my router to use WPA and WPA2 and still can't get 10.4 to connect to it.

Is it possible that certain, ancient, wireless cards just wouldn't work with this?

In other troubles...10.4 doesn't seem to have a driver for the Trident CyberBlade Ai1 video card, so I'm stuck at 800x600 resolution.  Other than running the Harware Drivers application, is there anything else I can do for this?

---

