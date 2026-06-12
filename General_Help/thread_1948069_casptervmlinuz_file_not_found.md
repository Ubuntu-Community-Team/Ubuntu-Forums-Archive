---
title: "/caspter/vmlinuz file not found"
date: 2012-03-27
forum: General Help
---

### Post by NickTheMajin on 2012-03-27
So I have been trying to partition ubuntu on my computer. I burned the iso of ubuntu onto a DVD (After md5 check summing it to make sure and it checked out). I set my boot order to boot from cd/dvd and it loads. And then that message, "caspter/vmlinuz file not found" pops up. 

This is my second time trying to install ubuntu today. The first time the cd had this issue but I restarted and it went through all the way up through to when it asked me to choose a keyboard layout where it crashed. I checked windows and the partition did affect the amount of space I have on windows, but I can't boot into linux and trying to use the dvd to redo it just yields the casper/vmlinuz file cannot be found. 

I have creating an iso from my dvd to make sure it burned correctly and it also passes md5 check sum. Any hints?

---

### Post by cholericfun on 2012-03-27
well, when you open the iso - is there a casper/vmlinuz file?

---

### Post by NickTheMajin on 2012-03-27
Yes I just checked. There is a vmlinuz file in the casper folder

---

### Post by cholericfun on 2012-03-27
sounds a bit odd - have you been trying the LiveCD first. Did you have any issues?

---

### Post by NickTheMajin on 2012-03-27
Not sure what the live cd is. I downloaded this file...
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
Far left, download and install. For 32bit oses. And didn't want to mess with virtualization. I just wanted to put it right on my computer.

And it kind of worked earlier. It got me all the way through the set up process to the point where it even partitioned my hard drive but it crashed when it asked me about my keyboard choice.

---

### Post by cholericfun on 2012-03-27
when you boot with the cd it should give you options like "Install" or "Try ubuntu without changin anything on your computer". The latter is the famous LiveCD.

Maybe give it a try just to see it that works, at least something to try out until someone with a better idea gets around...

---

### Post by NickTheMajin on 2012-03-27
Doesn't even give me that option. I get this message before that

---

### Post by cholericfun on 2012-03-27
also with the cd?

---

### Post by NickTheMajin on 2012-03-27
Yes with the cd. It doesn't give me any options. it shows a small graphic on the bottom and then that error pops up.

---

### Post by cholericfun on 2012-03-27
sounds like some rare nasty problem,
maybe have a go at an older distro and then upgrade.
maybe using an usb to not waste cds.

---

### Post by NickTheMajin on 2012-03-27
So is there a step by step guide I should follow on how to use a usb device. The only ones I saw were how to make a temporary linux. I want a full permanent partition. Also can you link to a previous one you would recommend and how to update after.

---

### Post by cholericfun on 2012-03-27
oh - well, thats what i meant- a usb for installing, just like a cd. never mind, i just find it a relatively handy tool (as long as it works) - especially if trying out different versions or distributions.
(also i dont have a cd-burner...)
but thats not really the point, i recon its best to try out an older version. Thats not a very good attempt at a solution but apparently theres not much by way of imaginative problem solving even on web-searches for this.

---

### Post by dRako1337 on 2012-04-08
jep same problem here!

---

### Post by Kyslosh on 2012-09-25
I had same problem I think this will solve the issue,
[https://answers.launchpad.net/unetbootin/+question/161465](https://answers.launchpad.net/unetbootin/+question/161465)

or let me quote from the site (if dead in future)

> Did you check the downloaded iso file with md5sum?
Sounds like you got the boot menu, but then the kernel was not found in the compressed filesystem, so maybe a bad file.
Do you ever see an option to run mediacheck? Try that if you see it. Usually CDs have media problems, but usb sticks can have media problems too. Which installer did you use? unetbootin seems to work for most people -- I've used it myself on a Linux system, never on a Windows system though.

my md5sum is good, I burned mine CD at highest speed 52x (or 48x), ATM I am burning at 8x and I hope the result will be good :) 
(I'll update thread)

//edit: slower burning speed helped ;) **just burn ISO at lower speed (8x)** and you are all set.

---

### Post by Vicolaships on 2013-03-26
Hey there, same problem here today, just go inside your USB stick and** rename** :

/casper/vmlinuz/**vmlinuz.efi**
 /casper/vmlinuz/**vmlinuz**

Bye bye :)

EDIT: Sorry for the bump, I misread the date :S

---

### Post by rgrigga on 2013-03-26
Had the same problem; this worked for me:

[http://choorucode.com/2013/03/17/caspervmlinuz-file-not-found-error-on-ubuntu-desktop-12-04-2-lts-installation/](http://choorucode.com/2013/03/17/caspervmlinuz-file-not-found-error-on-ubuntu-desktop-12-04-2-lts-installation/)

---

