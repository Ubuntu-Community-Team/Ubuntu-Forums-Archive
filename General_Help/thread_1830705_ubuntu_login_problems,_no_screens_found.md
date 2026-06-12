---
title: "ubuntu login problems, no screens found"
date: 2011-08-22
forum: General Help
---

### Post by surrealillusions on 2011-08-22
Hey all,

I've got a problem when trying to boot up ubuntu 10.10 on one hard drive when plugged into another computer. The main computer it runs in has an ATI graphics card, but the CD drive doesnt appear to work. So, switching the HD over to another computer where the CD drive works, and it doesn't boot up.

I get a black screen with the tty1 login. After some searching, and many failed attempts, I typed in my username and the password worked, wahey! Then tried startx but got a couple of errors. Trying 'sudo service gdm start' that afterwards resulted in:
"start: Job is already running: gmd"

> (EE) No supported AMD display adapters were found.
(EE) No devices detected

Fatal server error:
no screens found

Now I'm stuck again. Any ideas to get me logged in?

---

### Post by Wayne_V on 2011-08-22
You need to reconfigure you video card driver:  [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by surrealillusions on 2011-08-22
Hmm...doesnt appear to work..

sudo dpkg-reconfigure xserver-xorg

Doesn't produce any questions. I just get the next line

username@desktop:~$

awaiting another command.

Tried doing it again, double checking the spelling, but still nothing.

---

### Post by Wayne_V on 2011-08-22
I see now that is for older versions of X.  Try just 'sudo Xorg -configure':   [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by surrealillusions on 2011-08-24
Still nothing. Getting the same errors as before with the no screen found, no supported amd driver and no devices detected.

---

### Post by Wayne_V on 2011-08-24
did 'sudo Xorg -configure' create a new xorg.conf file for you? (see 'man xorg.conf')

What is in your /usr/lib/X11/xorg.conf.d directory?

---

