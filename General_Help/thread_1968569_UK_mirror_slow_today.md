---
title: "UK mirror slow today?"
date: 2012-04-29
forum: General Help
---

### Post by hal8000 on 2012-04-29
Anyone experiencing slow downloads and updates from the UK mirror service today?
I have ADSL connection my download rate is generally about 820kB/sec using apt-get today, I'm only seeing about 12kB/sec.

Just installed 12.04 so its almost certain to be new demand for Ubuntu.

---

### Post by Monotoko on 2012-04-29
Hey Hal,

I've noticed it's been mind-crushingly slow for the last few days as well.

Mono

---

### Post by grahammechanical on 2012-04-29
Think of all those people in a hurry to download 12.04 or upgrade to 12.04. It is most definitely causing bandwidth problems when connecting to Ubuntu servers. Updating the package lists is taking minutes instead of seconds as it used to. It reminds me of my dial-up modem days.

@hal8000

Looking again at your post, I see that it is all your fault. :)

Regards.

---

### Post by Monotoko on 2012-04-29
Which servers aren't being hammered? Is there a way to do a temporary switch?

---

### Post by PaulW2U on 2012-04-29
> **hal8000 said:**
> Anyone experiencing slow downloads and updates from the UK mirror service today?
I have ADSL connection my download rate is generally about 820kB/sec using apt-get today, I'm only seeing about 12kB/sec.

Just installed 12.04 so its almost certain to be new demand for Ubuntu.
Yes, my cable connection is also seeing very slow download speeds from the UK servers. It's been this way since Thursday, the day of 12.04's release. Speeds seem to be increasing slowly though.

---

### Post by hal8000 on 2012-04-29
Thanks for reply Mono,
I just tested my broadband and its running close to maximum speed.
I'll wait a few days until I update I think.
Hal

---

### Post by =NickJ= on 2012-04-29
Open the Software Center -> Edit -> Software Sources

Change "Download From" to "Main Server".

I'm now running at 1.4MiB/sec whereas on UK server I was on 30KiB/sec :|

---

### Post by Monotoko on 2012-04-29
Hi NickJ,

Thank you! I might have a go at the clean install on my second machine now :)

Mono

---

### Post by ubiquitin.jf on 2012-04-29
The "Select Best Server" button in Software Sources will test all the servers in the UK for you and select the fastest one for you. You'll get better speeds and not put so much stress on the poor main server this way.

---

