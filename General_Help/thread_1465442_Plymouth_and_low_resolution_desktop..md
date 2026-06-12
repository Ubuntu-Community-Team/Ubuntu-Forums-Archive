---
title: "Plymouth and low resolution desktop."
date: 2010-04-29
forum: General Help
---

### Post by lockalidiot on 2010-04-29
I have issue with ubuntu booting only to low graphics mode. As in desktop resolution = 640x480. I also had d*** ugly boot splash that was off center and about res 800x600. Then I tried this workaround **elkikin** posted in another thread.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Result is: Desktop resolution as it should be 1280x1024*(at least this time. I have done only one boot after this workaround.**{see EDIT}***), Grub splash*(where you choose which OS to boot to*) is 1280x1024 and boot splash*(plymouth)* is centered and **640x480**!!!!! I'm a bit lost here.

I am running Lucid 64-bit RC, with all available updates. Using NVidia GeForce 220 gt graphics card. The drivers are as they should be and when I'm lucky enough to have my box to boot in high res mode they seem to work. I have tried reinstalling them every now and then to no avail.


**EDIT**: Added an attachment on the error message I get when this bugger doesn't boot normally. Unfortunately this "low res" boot seems to bee the more common for me now. Three times in a row now.

---

### Post by clhsharky on 2010-04-29
HI


Known issue, Some one mentioned a work around.

[http://ubuntuforums.org/showthread.php?t=1451820](http://ubuntuforums.org/showthread.php?t=1451820)
[http://ubuntuforums.org/showthread.php?t=1457365](http://ubuntuforums.org/showthread.php?t=1457365)

sharky

---

### Post by lockalidiot on 2010-04-29
Thanks a million! I've been trying the search google and these forums upside down to get this issue solved, but nothing showed up.
*running to see the threads*
:P

---

### Post by lockalidiot on 2010-04-29
Ok, I checked those threads out. Turns out that the first one was the one where I found the workaround I mentioned in my first post. The second I have also read before. I don't so much care about my "boot experience" at this point. What is really bugging me is that the OS's UI I boot to has a very small resolution. It is damn close unusable!

_Please see the attachment of the first post_. That is what I get AFTER the boot is over. Then I click OK, choose either option to *"run Ubuntu on low graphs mode just this once"*
or to *"restart X"*
the result is always as below.
_Then see attachments of this post._ This is what I get. Ad this is now pretty much every boot. Other attachment is with docky on and the other after I run:
```
killall docky
```

EDIT: darn, I forgot to upload the attachments... Here we go! 
EDIT2: Also added one more, to show how it should look like.

---

### Post by lockalidiot on 2010-04-29
Further update, I'm now downloading all the new updates that will make my RC a Final Release. Fingers crossed it will also solve this issue. If not, I'll add an EDIT to this post.

---

