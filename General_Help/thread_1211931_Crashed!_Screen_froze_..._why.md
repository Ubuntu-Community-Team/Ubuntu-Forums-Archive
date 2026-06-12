---
title: "Crashed! Screen froze ... why?"
date: 2009-07-13
forum: General Help
---

### Post by zcacogp on 2009-07-13
Chaps, 

My machine just crashed. 9.04, X61s Thinkpad lappie. I had just locked it, it was running a screensaver (BioF - one of the standard ones), and the screen froze. I pushed various buttons, clicked the mouse and swore a little, then pulled the power supply out (battery not plugged in at the mo) and re-started.  

I thought that Ubuntu was meant to be stable, and this sort of thing wasn't meant to happen? I've been using Ubuntu for the last 3 months or so, and while it is generally getting better this isn't the first time I have had a crash. I came over from Win XP, which never crashed on me to my recollection (despite the reputation it has.) 

I know I'm not posting much information on here, but if someone can tell me where to find a system log I can put the contents up here. I'd quite like this not to happen again (didn't lose work but it's not helping my confidence in the system.) 


Oli.

---

### Post by miklcct on 2009-07-13
Ubuntu 9.04's kernel is particularly problematic so I grabbed the kernel in Karmic and installed it, then my machine no longer hangs.

---

### Post by zcacogp on 2009-07-14
Miklcct, 

Thanks for your reply. 

I am a bit of a beginner with this sort of thing; I don't actually quite understand what you suggested, let alone how to do it. (I suspect this means I shouldn't try doing such stuff, as if I do and it breaks then I won't be able to fix it, eh?!) 


Oli.

---

### Post by agwblack on 2009-07-14
A friend of mine has been having similar problems with Linux Mint 7, which is based on Jaunty and uses the same kernel. From what I read, the kernel has some problems with some proprietary graphics card drivers, and this is may be what is causing the problem.

Are you using proprietary drivers? Disabling them may fix the problem.

I'm much too much of a newbie to know about getting a different kernel. But that doesn't mean you shouldn't try! Search around the forums for how. Its the best way to learn. Just make sure you back everything up so that if you need to reinstall your system (see below), then you won't lose your data.

Alternatively (and this is what I will try on my friend's computer this evening) you can just reinstall an older version of ubuntu (intrepid). Hopefully, you have a separate /home partition with all your data on it, so you don't lose everything? If not, again just back everything up and copy it across once you've completed your new install.

Let's see what happens, eh?

Andy

---

### Post by agwblack on 2009-07-14
The main thread for this problem would seem to be here: [http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+crash](http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+crash)

Happy reading!

Andy

---

### Post by agwblack on 2009-07-14
One solution that seems to have worked for most who have tried it: follow this thread through upto and including step 3. [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

This should update your kernel to 2.6.30. Apparently this fixes the problem. Don't be scared - the worst that'll happen is you have to reinstall intrepid anyway, so even if everything dies (which there is no reason it should) then you're no worse off. Just remember to back up your data first!

Now, I should really get back to work...:wink:

Andy

---

### Post by zcacogp on 2009-07-14
Andy, 

Whoah! Thanks. That looks like an evening's worth of work ... I'll try and have a pop some time this week. 

Thanks for the pointer. 


Oli.

---

### Post by rhchia on 2009-07-14
woo... that some light for the lost me. i encoutered this problem when i tried to install my brother printer driver (DCP-115C). the scanner still does not work and the crash happen quite often and i tot its the problem with the scanner. today i was looking around for gtkmm programming when it suddenly crash twice. 
thanks for the link and i'll check out the solution on my spare time.
zcacogp, if you had tried the solution don't mind you share your experience with us. thanks! :p

---

### Post by zcacogp on 2009-07-14
> **rhchia said:**
> zcacogp, if you had tried the solution don't mind you share your experience with us. thanks! :p

Trust me, you shall hear the wails of anguish all the way from London. (That's the UK. I'm guessing you - like most on here - are state-side. ;) ) 


Oli.

---

### Post by zcacogp on 2009-07-16
OK. Done. Followed the instructions on the page given by Andy (here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) ). I went to Part C, so am now running the "Optimal/Bleeding-Edge" settings. And ... well, it all seems the same as before. The sun is still shining. The cat is still asleep. My cup of tea still tastes of tea. 

Importantly, the laptop still works. It isn't broken. (I re-started. Was this necessary, or just a throwback to my Windows days?) It started OK. It has yet to crash, but has only been running for :Checks: 6 minutes. 

I guess the proof of the pudding is in whether it crashes again or not. The thread linked to suggests that the machine may go a little quicker, which would be nice but I have seen no evidence of it. But then I haven't been looking either. 

A question tho'. When I downloaded the new kernel files, using this command: 

```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```

... where did it store the files it downloaded? There are three of them (I think), and if I do this to another machine (which I will), I would like to re-use the files rather than downloading them again. They are presumably saved on this machine, and I could copy them to other machines, but where do I find them? (I appreciate that the link posted is for the i386 - Intel - files, and if I do the same with an AMD-chip machine I will need to use another set.) 

Thanks for your help. Andy particularly. We'll see whether this configuration is any more stable. 


Oli.

---

### Post by xflyboy on 2009-07-16
> **zcacogp said:**
> OK. Done. Followed the instructions on the page given by Andy (here: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) ). I went to Part C, so am now running the "Optimal/Bleeding-Edge" settings. And ... well, it all seems the same as before. The sun is still shining. The cat is still asleep. My cup of tea still tastes of tea. 

Importantly, the laptop still works. It isn't broken. (I re-started. Was this necessary, or just a throwback to my Windows days?) It started OK. It has yet to crash, but has only been running for :Checks: 6 minutes. 

I guess the proof of the pudding is in whether it crashes again or not. The thread linked to suggests that the machine may go a little quicker, which would be nice but I have seen no evidence of it. But then I haven't been looking either. 

A question tho'. When I downloaded the new kernel files, using this command: 

```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

```

... where did it store the files it downloaded? There are three of them (I think), and if I do this to another machine (which I will), I would like to re-use the files rather than downloading them again. They are presumably saved on this machine, and I could copy them to other machines, but where do I find them? (I appreciate that the link posted is for the i386 - Intel - files, and if I do the same with an AMD-chip machine I will need to use another set.) 

Thanks for your help. Andy particularly. We'll see whether this configuration is any more stable. 


Oli.

I'm not a prof. but they should be in the folder where you were when you DLd them. Ex. $HOME dir.
> max@dell:~$ ls
ati-driver-installer-9-3-x86.x86_64.run                     Music
Desktop                                                     Pictures
Documents                                                   Public
examples.desktop                                            Templates
[COLOR="Red"]linux-headers-2.6.30-020630_2.6.30-020630_all.deb           Videos
linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb  xf86-video-radeonhd
linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb[/COLOR]

---

### Post by agwblack on 2009-07-24
Has it crashed yet, Oli?

---

### Post by zcacogp on 2009-07-26
agwblack, 

Thanks for asking. 

No. 'Tis fine. New kernel install went like a swiss watch, and all has been well since. Problem (possibly/probably) solved. 

(I then got all gung-ho and tried to do the same on my desktop machine. Which trashed it. So I re-installed, and discovered that there was a conflict with the screen driver I had installed, and thus trashed it again. I managed to uninstall the screen driver that time, and have now got it back, but it's not quite right. Not as good as before, for sure. Not quite sure where to go with it now. 

Threads galore here: 

[http://ubuntuforums.org/showthread.php?t=1219209](http://ubuntuforums.org/showthread.php?t=1219209)
[http://ubuntuforums.org/showthread.php?t=1214868](http://ubuntuforums.org/showthread.php?t=1214868)
[http://ubuntuforums.org/showthread.php?t=1221829](http://ubuntuforums.org/showthread.php?t=1221829)   )

I'll keep this thread updated if things do go nipples-upwards on the lappie again. 


Oli.

---

