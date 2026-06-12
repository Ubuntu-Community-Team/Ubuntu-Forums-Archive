---
title: "S-video out with laptop not working"
date: 2006-06-17
forum: General Help
---

### Post by ask1 on 2006-06-17
Hi,  I'm new to linux.  I recently installed Dapper on my Compaq laptop, and I cannot get the s-video (tv-out) to work.  When I press the FN-F4 command, nothing happens.  The graphics chipset is ATI Mobility 9200.

I've tried booting up my laptop with my TV on and connected, but it still didn't work.

(Also, I'm sure nothing is wrong with the hardware because it worked fine with Windows XP).

Could anyone help me out?
Thanks.

---

### Post by ask1 on 2006-06-17
btw, I also tried installing the drivers from ATI.com, but after running aticonfig --initial and rebooting, the screen was all messed up, so I had to boot into recovery mode and uninstall it.

I've searched the forums, and it doesn't look like anyone knows the solution.  Looks like it's back to Windows XP.  Oh well, it was fun while it lasted.

---

### Post by IMELucky on 2006-06-22
Im also having the same proble with my HP Compaq nc6230 with ATI chip. Is there a way to configure XOrg for TV display?

---

### Post by jocko on 2006-06-22
I'm not sure this will help you, but it's worth a try...
First make sure you have ati's drivers installed and working properly. The easiest (and probably best) way is to install xorg-driver-fglrx using synaptics or apt-get (in my experience running the binary from ati.com usually mess things up).  There are probably dozens of threads in this forum that will help you with getting it working.

When it's working try issuing these commands (without my #comments) in a terminal:

```
sudo aticonfig --tvf=PAL-B #change this to your local TV-format
sudo aticonfig --tvs=VIDEO          #for S-video output
sudo aticonfig --force-monitor=tv #force TV-out, even if TV is not detected

```

Restart xorg (ctrl-backspace) and keep your fingers crossed.
To get more help on the options for aticonfig, just run ```
aticonfig --help
```
Hope this helps you...

---

### Post by xtacocorex on 2006-06-22
Here is a Gentoo guide on the 6220 computer, but it doesn't mention s-video, but at least it's a start for you all

[http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nc6220](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nc6220)

Also, here is one about the 6220 on Breezy: [https://astibharath.org/blog/ubuntu-breezy-on-hp-nc6220/](https://astibharath.org/blog/ubuntu-breezy-on-hp-nc6220/)

It seems that they couldn't get it working either.

Other than that, I can't offer any other help because I haven't tried getting s-video to work on my Dell.

---

