---
title: "errno 5 ... please help, i'm at my very end"
date: 2012-01-09
forum: General Help
---

### Post by hardisty on 2012-01-09
I've been trying to install Ubuntu 11.10 all day now. Initially starting with trying to get a dual boot but now I'll take anything. Every time I try installing I get an Errno 5 message. If I boot from Live USB and check for disk defects, it'll tell me that I have 1 error but it won't say what it is. I've reformatted constantly. Made new USB after new USB after new DVD after new CD etc. It's enraging me and the stress is ridiculous. I've tried different Ubuntu versions and it's all the same. I have no idea what the hell I can do. Googling has given me nothing.


Help me, Ubuntu Forums, you're my only hope!


Thank you!

---

### Post by Quackers on 2012-01-09
If there is a single fault with the cd that can be enough to stop an installation.
Firstly I would check the md5sum of the downloaded .iso file and if that checks out I would re-burn the image at the slowest possible setting.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Silent Warrior on 2012-01-09
If Quackers' advice doesn't work for you, you might as well test another distribution. There are plenty of Debian- and Ubuntu-derived ones out there (consult distrowatch.com), but, to play it safe, you should also see if openSUSE, Fedora, or other big name distributions will install.
If nothing works, be afraid, for then it's likely a problem with your computer or USB device. Thousands have been able to install from these images, after all.

---

### Post by hardisty on 2012-01-09
> **Quackers said:**
> If there is a single fault with the cd that can be enough to stop an installation.
Firstly I would check the md5sum of the downloaded .iso file and if that checks out I would re-burn the image at the slowest possible setting.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


It produced the same hash but if I try to burn to DVD now either nautilus or brasero will crash upon clicking "write to disc" or "open with brasero", respectively.

---

### Post by hardisty on 2012-01-09
> **Silent Warrior said:**
> If Quackers' advice doesn't work for you, you might as well test another distribution. There are plenty of Debian- and Ubuntu-derived ones out there (consult distrowatch.com), but, to play it safe, you should also see if openSUSE, Fedora, or other big name distributions will install.
If nothing works, be afraid, for then it's likely a problem with your computer or USB device. Thousands have been able to install from these images, after all.

put it just came out of nowhere during a reinstall. what could have happened? how do i fix it? ggaaahhhh i think i need sleep

---

### Post by hardisty on 2012-01-09
> **hardisty said:**
> put it just came out of nowhere during a reinstall. what could have happened? how do i fix it? ggaaahhhh i think i need sleep

put = but

---

### Post by pretty_whistle on 2012-01-09
> **hardisty said:**
> It produced the same hash but if I try to burn to DVD now either nautilus or brasero will crash upon clicking "write to disc" or "open with brasero", respectively.
Well, I've had no installation problem.  I used K3b to burn the iso each time.  FWIW.

---

