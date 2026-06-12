---
title: "blank screen on resume from suspend mode"
date: 2010-06-08
forum: General Help
---

### Post by Andrew Golightly on 2010-06-08
Title says it all. I close my laptop lid. It goes into suspend mode. I open it up again, the computer powers up... and I see a black blank screen. No key combinations seems to bring anything back.

So I have to do a hard reset. Any ways to get the screen coming back??

thanks.

---

### Post by jrab227 on 2010-06-08
This isn't an Ubuntu problem only. The same thing happens on my Acer A1 with Jolicloud. It has to do with the video card not being re-initialized after suspend, and its somewhere in the scripts. I attempted to find out whats up online, but it seems users are solving the problem on an individual basis and getting results, so at least we know its fixable. I haven't done it myself but hopefully someone can tell how to fix this.:(

Also as far as I know, using Ctr-Alt-F1 should bring up a bash. From here I don't know a command to bring back your GUI except for attempting Ctr-Alt-F7. I haven't tried it but its worth a try. A command that restarts your distro's GUI might do the trick as well.

---

### Post by fanny4545ff on 2010-06-08
I think its a not a any big problem so you want a good computer engineer only he can solve your problem.
                             thanks

---

### Post by jrab227 on 2010-06-10
bump

---

### Post by jrab227 on 2010-06-19
bump

---

### Post by dajare on 2010-06-20
I'm desperately hoping for an answer to this one, too.

I've been on 9.04 happily for quite some time (Toshiba Satellite A100). Today, for some reason, I decided to "Suspend" instead of shutdown. Now NOTHING will restore it: ONLY black screen.

I have searched thread after thread. No key combination will force a shut down, or give back display. I've tried power-key-off and then running live disk from CD drive. Black screen. I've tried FN keys to alter display. Nothing.

I'm not *quite* at hurling-self-off-bridge point yet ... but I'm getting there.

---

### Post by fazio93 on 2010-06-20
same problem here. still looking for a solution. : (

---

### Post by dajare on 2010-06-20
Right - well at least I'm back in business ... NEVER to use "Suspend" mode in Ubuntu again!

Since it takes battery power to keep the stored session in RAM, the solution was to power down, unplug (which I had done before), AND take out the battery (which I had not), and leave for a while.

Starved of power, the suspended session simply disappeared, and on powering up again, I got the familiar cold boot.

PHEW!

Truth be told ... my daughter found the solution -- well on her way to being a girl geek, it seems! =D>

---

### Post by sf_basilix on 2010-06-23
I am having the same issue with Ubuntu 10.04 64 bit (lucid) on a Dell Latitude e6510 with Intel Core i5. It appears to suspend fine, but resuming just returns a black screen. No keystrokes wake it up, can't even ssh in.

For what it's worth, I installed Ubuntu 10.04 32 bit on a lenovo R61i laptop and it worked fine there.

---

### Post by lordskid on 2010-06-23
did you try to press the power button? I did the same thing... close the lid, then open it up. the machine seemed to power up. but I get a blank screen. so I press the power button. I got the password prompt. key in my password and everything was back to when I left my laptop.

---

### Post by Robert Ayrapetyan on 2010-06-25
I have very similar issue on desktop PC with Ubuntu 10.04 - when PC returns from suspend mode I sometimes see blank screen. There is also some high hdd activities this moment (it's bloody similar to something like scandisk), and after 5-10 minutes blank screen dissapears and I can see standard gnome login window.
UPD: Several seconds before returning to login window I always see red square composed from red dots\lines at the top left corner, seems like an artifacts in videocard buffers.

---

### Post by jrab227 on 2010-06-30
I actually think I found a semi decent link explaining the problem with good solutions here. Please try it out and let me know if it works.

[http://superuser.com/questions/36296/troubleshooting-failure-to-standby-suspend-with-ubuntu-netbook-remix-on-acer-aspi](http://superuser.com/questions/36296/troubleshooting-failure-to-standby-suspend-with-ubuntu-netbook-remix-on-acer-aspi)

---

### Post by shabeebrizvi on 2010-07-16
This is frustrating.... I have the same problem and visited almost all the available thread over Internet... and it seems this has been a problem since 2006... in all version at least from 7.xx onwards as per what i have found.... There were few solutions to the problem posted but nothing worked fro me.... 

Are we saying there is no GEEK left on this entire Internet world who has solution for this ???

I am now stuck from Windows Blue Screen to Linux Black Screen......  ](*,)

---

### Post by hoovenator on 2010-07-17
Same problem here on y530 with nvidia 9300...noticed also on fedora 12 and 13 installs. All tried in 32 and 64 bit.

---

### Post by sf_basilix on 2010-09-02
I did press the power button as well as virtually every other button on the keyboard, but it just wouldn't come back.

---

### Post by PhaseMod on 2010-09-25
This is happening to me also with standby and hibernate on a Lenovo ThinkPad X41 with a wubi netbook 10.04 install. No matter how the standy or hibernate are triggered the screen is blanked (but still on) and the sleep indicator light on the notebook flashes but never fully enters the standby or hibernate as far as I can tell (power seems to be drained as if the system were still running normally). It's completely unresponsive to any keyboard strokes or the power key. Only the programmers interrupt or a full power off holding the power key several seconds allows me to escape this lockup which results in a full startup of course.

---

### Post by PhaseMod on 2010-09-25
OK, I hadn't seen this before but the link that jrab77 included had the source of my problem. I nearly always have an SD card in my notebook and the kernel for netbook 10.04 is trying to umount it and failing each time on suspend/hibernate. Need to compile our own kernel as it mentioned it seems:

"Enabling UNSAFE_RESUME in the kernel options for MMC device drivers will  stop the kernel from unmounting SD/MMC cards before suspend."

Would prefer to see that behavior as a default as the risk for that seems to be mostly those using ext2/ext3 file systems on their SDs (or those that like to eject SDs while it's suspended).

After unmounting and ejecting the SD card suspend and hibernate appear to be working as they did before 10.04.

---

### Post by wilsonB on 2012-06-14
This works for me when unmounting / ejecting the SD card.
Ubuntu 12.10



Now;
"Enabling UNSAFE_RESUME in the kernel options for MMC device driver

How do I do that? In grub?

---

### Post by overdrank on 2012-06-14
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

