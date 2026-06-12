---
title: "Watchdog Error Message?"
date: 2012-05-01
forum: General Help
---

### Post by cottfcfan on 2012-05-01
When Waking from Suspend, I have 3 error messages appear about Watchdog.
When I ran dmesg I found this:
```
[18507.824679] watchdog: only one watchdog can use /dev/watchdog.
[18507.824684] watchdog: error registering /dev/watchdog (err=-16).
[18507.824687] mei: unable to register watchdog device.

```
Does anyone know what this is?
Is it important?
Will it affect my system?
This has only started happening in 12.04.

---

### Post by jim_24601 on 2012-05-01
Yes. It seems to be benign, but it's annoying.

A little digging turns up [this thread on Arch]("https://bbs.archlinux.org/viewtopic.php?id=133083") which goes into a fair bit of detail about the problem. According to the discussion there, the problem is that you've got two watchdog drivers loaded but the kernel supports only one at a time. Blacklisting the "mei" module should make the messages go away. I will try it and report back.

---

### Post by cottfcfan on 2012-05-01
Thanks for looking at this Jim.
I will wait to hear from you.

---

### Post by jim_24601 on 2012-05-01
OK. Seems to work. I created the file '/etc/modprobe.d/mei.conf' containing the line
```
blacklist mei
```This silenced the annoying barking from the watchdog.
It seems a bit of a cop-out, but my efforts to dig deeper into the problem left me none the wiser, and since both watchdog and MEI are firmly in the "why do I even *have* one of those?" category right now as far as I'm concerned, I'm not planning on spending any more time on it. :)

---

### Post by cottfcfan on 2012-05-02
> **jim_24601 said:**
> OK. Seems to work. I created the file '/etc/modprobe.d/mei.conf' containing the line
```
blacklist mei
```This silenced the annoying barking from the watchdog.
It seems a bit of a cop-out, but my efforts to dig deeper into the problem left me none the wiser, and since both watchdog and MEI are firmly in the "why do I even *have* one of those?" category right now as far as I'm concerned, I'm not planning on spending any more time on it. :)

Thanks that seems to work.
Actually you can add "blacklist mei" straight to /etc/modprobe.d/blacklist.conf, without creating a new folder.
Thanks for all your help, i'll mark the thread as solved.

---

### Post by Jaredtinari on 2012-08-15
Hey there,
I'm pretty new to Ubuntu and linux altogether. Ive been having the same watchdog error message upon resume and although its benign, I like everything to be as perfect as possible. Can you just instruct me on what exactly i type into terminal? Where do I add the "blacklist mei"? All help is greatly appreciated!

thanks!:D

---

### Post by cottfcfan on 2012-08-15
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
add the line:
"blacklist mei" without the quotes to the bottom of the file.
Save & reboot.

---

### Post by nousplacidus on 2013-01-01
For those of you who are wondering what the consequences of blacklisting the MEI driver will be, there's a short explanation of the purpose of the MEI computing resource here:

[http://lwn.net/Articles/440292/](http://lwn.net/Articles/440292/)

In short, it's there to support IT management. If IT isn't managing your box, you can blacklist is safely it seems.

---

### Post by Polydorus on 2013-01-08
I'm getting the following message, using dmeg, after startup:

mei: module is from staging directory, the quality is unknown, you have been warned.

The only harm seems to be a bit slower startup.  Is there anything I should do about it?

TIA

---

### Post by invictuschamp on 2013-07-06
does this breach any security?

---

### Post by speartip on 2013-07-07
> **invictuschamp said:**
> does this breach any security?
Not that i'm aware of.
The other way to get rid of this message is to update to a later kernel.
In the backports there is kernel 3.5xx & 3.8xx.

---

