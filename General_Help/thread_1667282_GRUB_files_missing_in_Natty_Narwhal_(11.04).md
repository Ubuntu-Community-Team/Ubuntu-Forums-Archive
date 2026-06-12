---
title: "GRUB files missing in Natty Narwhal (11.04)"
date: 2011-01-14
forum: General Help
---

### Post by jcracken on 2011-01-14
I am a noob to Ubuntu, so I might just be doing something wrong. A couple months ago, I created a dual boot between Windows 7 and Ubuntu 10.04 using wubi. I then upgraded to 10.10. What would usually happen is I would start up my laptop and it'll go to the Windows boot manager, letting me choose between Windows 7 and Ubuntu. If I would choose Ubuntu, it would go to a GRUB boot manager. It would let me choose between several different ways to boot Ubuntu, mainly that there were different options that were all the same except they had different numbers in the name, i.e. Ubuntu, whatever, 14.33.22.19.25 or something like that. A couple weeks ago, I updated to 11.04. At first it worked good, but then a couple days later I updated a bunch of packages. It tried to CAT a GRUB file and failed. It gave me an error code, but I ignored it. Yesterday, I updated again, but since last time failed, it told me to do a partial upgrade. This I did, and it was successful. But now, everytime I go to GRUB and try to select any of the options, it tells me "Error: File not Found" and I cannot boot into Ubuntu. There are recovery versions for each choice, and using these I can boot into Ubuntu in low graphics mode and I can also get to a command line prompt. What can I do to fix this?

---

### Post by wilee-nilee on 2011-01-14
So you can't downgrade Linux in general, and especially a wubi you can't get to. You can get to its files in windows though to pull out what you want to have in a regular dual boot. I can help you with a dual boot, or others will. Just start with getting a Live install cd of anything from maverick to lucid, boot it to a try ubuntu session. Go to system-admin-gparted and take a screen shot of it and post it.

---

### Post by jcracken on 2011-01-14
I booted Ubuntu in failsafe graphics mode and got this. Also, I found out that I can boot Ubuntu regularly if I left it on the screen where it says "file not found" for a couple seconds and then pressed any keys. It won't load unity, however, so I have to select ubuntu classic desktop when logging in.

---

### Post by wilee-nilee on 2011-01-14
Is that from a booted cd or the failsafe in the wubi?

I see a red button on sda2 though right click it then information, you probably need a chkdsk /f/r run in windows, gparted is not reading it.

I need the live cd booted and that gparted to feel comfortable, as I'm not a wubi user nor do I know its limitations.

---

### Post by jcracken on 2011-01-14
I tried using a Live CD but I get mounting errors. Also, when I try to get an update, it tells me to do a partial upgrade again. If I do so, it says that ubuntu-desktop cannot be installed. I ran the partial upgrade several times, that's the only package left that can be installed. If I say no to the partial upgrade, it gives me an error. I took a screenshot of both that and of the error message given off by the red button.

---

### Post by wilee-nilee on 2011-01-14
What is the mount error of the live cd of Ubuntu?

How did you burn the CD?

You can load the live ISO to a thumbdrive as well.

Your trying to fix something=natty which is not worth the hassle it is very unstable.

You have what appears to be a Windows setup that needs some basic maintenance done the
chkdsk /f/r
run.

We have to get the cart behind the horse here.

---

### Post by jcracken on 2011-01-16
> **wilee-nilee said:**
> What is the mount error of the live cd of Ubuntu?

How did you burn the CD?

You can load the live ISO to a thumbdrive as well.

Your trying to fix something=natty which is not worth the hassle it is very unstable.

You have what appears to be a Windows setup that needs some basic maintenance done the
chkdsk /f/r
run.

We have to get the cart behind the horse here.
I'll be away from my laptop for the next couple days, but i burned the iso using imgburn. Ignore the windows stuff, I'll deal with it myself. All I remember from the error is that it couldn't mount a filesystem. It starts up, goes to a purplish screen with a keyboard equaling a universal access icon on the bottom, and then gives me an error. It still gives me a command prompt, though.

EDIT: I looked into the Windows problem and now Windows won't start up, so I'm going to replace my hard drive. Doing so will get rid of everything on there, including Ubuntu. Thanks for helping though, next time I dual boot I'll stay on 10.10.

---

