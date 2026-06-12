---
title: "Fingerprint Log in"
date: 2010-02-05
forum: General Help
---

### Post by theadictspunk on 2010-02-05
Hi guys,

Im fairly new with Ubuntu and Linux. However, I am really liking it. 

I have a IBM Thinkpad t60. Stock (with windows) it let me log in with the fingerprint reader. It is something that i really liked; simple yet secure.

How, if possible, can i set that up with Ubuntu?

thanks

---

### Post by shriramrs31 on 2010-02-05
> **theadictspunk said:**
> Hi guys,

Im fairly new with Ubuntu and Linux. However, I am really liking it. 

I have a IBM Thinkpad t60. Stock (with windows) it let me log in with the fingerprint reader. It is something that i really liked; simple yet secure.

How, if possible, can i set that up with Ubuntu?

thanks

Its complicated. Many have gotten it to work and many did not. Its not as easy as it is in windows.

[http://ubuntuforums.org/archive/index.php/t-760018.html](http://ubuntuforums.org/archive/index.php/t-760018.html)

try the above one and also thinkpad wiki.

I too have a R61, with jaunty i got it to work. But after a fresh install of karmic, i had no interest to proceed with all the complicated stuff.

Let me know if any method works ;-)

---

### Post by theadictspunk on 2010-02-06
The fprint program worked perfectly :)

well, except for a small nic... I can't seem to get it to ask for another finger besides my right index... i've enrolled others... if i try to do the other anyways it wont work...

---

### Post by coldraven on 2010-02-06
Jaunty 64bit found my fingerprint reader but after a fresh install of karmic 64bit it is not found.
See: [https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/315921](https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/315921)
Does anyone knows why?

---

### Post by theadictspunk on 2010-02-06
Yeah, it did that to me too. Said it couldn't initialize my driver. 

On that same link up there, right under the write up, the author mentions the troubleshooting for that very same problem. Worked for me with the addition of doing a sudo fprint_demo instead of just fprint_demo just once and then restarting terminal and voila...


seems to be working fine for me now... but i still cant get it to read another finger

---

