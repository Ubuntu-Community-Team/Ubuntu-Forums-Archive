---
title: "grub2 very dissappointing"
date: 2010-09-09
forum: General Help
---

### Post by garyed on 2010-09-09
Maybe there is an easy way to work with grub2 but I haven't found it.
I have 2 laptops & 3 desktops all running some versions of Ubuntu for about 3 years now. Grub2 works flawlessly on some but on some it doesn't detect other OS's properly. What is the cure? The only thing I've found is to create a custom file to add something that wasn't picked up before.
I didn't start this thread as a complaint but I'm so puzzled by the change to grub2's complexity that I'm trying to see where the advancement is. Grub leagacy's menu.lst was easily editable & much simpler.
I have learned to get around grub2 a little but I keep asking the question "why?". I absolutely love Ubuntu & it is my primary OS but the only thing good I can see about grub2 it that its opened me up to working with other Linux distros.
After all this ranting let me ask this question:
How can I remove any OS from the menu that the grub2 30_os-prober picks up besides just not using it?

---

### Post by wkulecz on 2010-09-09
> I didn't start this thread as a complaint but I'm so puzzled by the change to grub2's complexity that I'm trying to see where the advancement is

I've complained about grub2 since it was first introduced.  Not ready for prime time IMHO.

The only actual thing it seems to do that grub legacy can't is boot powerPC machines, big whoop!

It breaks on a regular basis for me too, at least the documentation is starting to catch up and the only thing I can figure is you have no chance of it being reliable until you switch over to using 100% UUID mounts. 

I've a lot fewer issues since doing this but its a PITA when cloning systems and trying to reinstall grub2 as I sure can't type in things like 589da590-c54b-4cdb-b24b-278938cfde1e without a working cut and paste!

---

### Post by Rubi1200 on 2010-09-09
Take a look at this tutorial by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It goes into detail about how GRUB2 works, what you can change, and how (including doing what you want).

Hope this helps.

---

### Post by wkulecz on 2010-09-09
> **Rubi1200 said:**
> Take a look at this tutorial by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It goes into detail about how GRUB2 works, what you can change, and how (including doing what you want).

Hope this helps.

Perhaps my main issue is that grub2 should not have been foisted upon us until this level of documentation was available and then these docs should have been in a desktop shortcut on the installation CD to make the inevitable problems far less time wasting and frustrating.

---

### Post by garyed on 2010-09-09
I just don't understand why all the shell scripts like os-probing etc.. couldn't have been just another option to build or rebuild the menu.lst instead of a must. Sometimes update-grub works fine & sometimes not but editing the grub.cfg  file is a no no yet its O.K. to edit menu.lst. I like tinkering & actually enjoyed learning how to get around a little in grub2 but I don't see why its been forced upon us this way. I'm all for advancement but only if it serves a practical purpose. They replaced two grub legacy files with tons of files in /boot/grub/ for what? It almost sounds like I'm talking about Windows. I better stop before I get stoned.

---

### Post by WorMzy on 2010-09-09
There's no need to continue using grub2 if you prefer grub legacy. They're interchangeable.

I still use grub legacy because that's what I'm familiar with. I don't mind having to manually update menu.lst, it's hardly a complicated thing to do. It might not look pretty, but it does what it does, and it does it well.

---

### Post by Rubi1200 on 2010-09-09
Since GRUB2 is the way of the future, I personally recommend trying to get used to it.

However, as WorMzy points out, it is possible to still use legacy-GRUB.

This shows you how:
[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

---

### Post by wkulecz on 2010-09-09
> It might not look pretty

Ah, the root of the problem, bottom line is nobody really cares about the boot loader until it doesn't work!  Trying to "pretty it up" has introduced a lot of pain for no gain.

All the changes to the startup scripts have been a painful too, but at least they have an obvious benefit in speeding up the system boot, again not something most people really worry about, but at least this is a  measurable benefit to counteract the pain of the change.

IMHO grub2 fails the "if it ain't broke, don't fix it" test, big time.  But like Obamacare, its been forced upon us so just bend over and get used to  it.  Actually grub2 is way less painful than Obamacare :)

---

### Post by oldfred on 2010-09-09
I like grub2. But it had a longer learning curve as it offers more.

When grub first came out everyone said we had to stay with lilo. I did not particularly like grub2 as I had everything set up with chainloading to grub in the partition PBR. But grub2's osprober is very good at finding other systems.

With old grub we had lots of problems where those who thought they new what they were doing would mis edit the menu.lst and not boot. Or put their windows stanza inside the auto magic area and wonder why it got overwritten. They did not know there were configuration settings in menu.lst that they should be using. And for just about any other operating system we had to provide custom boot stanza. (Why I was chainloading). 

I now have moved most of my custom stanzas and copies of osprobers stanzas into 40_custom so I can edit at will. It is just as easily as editing menu.lst and not as complex of a file. I just keep forgetting to run sudo update-grub after every change.

---

### Post by QIII on 2010-09-09
> **wkulecz said:**
> But like Obamacare, its been forced upon us so  just bend over and get used to  it.  Actually grub2 is way less painful  than Obamacare
 
 Is there a politics sub forum?  Is this helpful to the OP?

Up front, the answer to the original question is here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

which was cited above.

Look for "/etc/default/grub".  Under that is a header: "GRUB_DISABLE_OS_PROBER="true"".  Make whatever changes you want in 40_custom, which is relatively easy to learn if you are familiar with menu.lst.
 
 You may use GRUB if you choose.  There is that option, and options are  what Linux is all about.  You can, and should, use what works for you.  I  heartily agree with your desire to use what works for you.  You have  every right to be disappointed in something that does not work for you.   That is the point.
 
 Perhaps there should have been a choice at install, so those who wanted  GRUB could stick with it.  Were the developers a bit heavy handed in not  leaving you that option?  Perhaps.  But there is always a danger in  sticking with the old and eschewing the new:  Being left at the platform  when the train leaves.  
 
 There is a philosophical issue here more than one of functionality.
 
 The very real and important question is not whether GRUB2 works.  It  most certainly does.  I've been using it for quite some time.  I  upgraded from GRUB before it became the default.  Yes.  I had to learn  new things.  Yes.  Some of it was hard to understand.  Yes.  I borked  things and had to rescue myself.
 
 The actual problem is that GRUB2 is simply *different *and behaves  differently than we grew accustomed to in GRUB.  Most of you had to  learn a whole new environment when you came to Linux in the first  place.  Do you remember that?  Things change.  They get improved.  The  improved things are *different *and do not fit your expectations if you insist that they not be different.
 
 I had to relearn how to turn on the high beams when the switch went from  the floor to a stalk on the steering column.  Different.  I had to  relearn how to turn the key when the switch went from the dash to the  steering column.  Different.
 
 GRUB2 is substantially more configurable, which means that there is more  to do.  More control often means more initial complexity.

---

### Post by garyed on 2010-09-09
The points are well taken on both sides. 
I guess maybe when all the kinks are worked out with Grub2 I'll feel a little different but for now it seems frustrating.
Here's one example: 
I've got a Desktop with Ubuntu 7.10 , 10.04, WinXP & Pclinux on it.
The os_prober picks up everything correctly but Pclinux, so I had to add a custom script for it to boot. Now I have a lot of stuff on my boot menu & some I don't need.  If I get rid of the os_prober then I'll have to manually add XP & 7.04 to the custom script also. If there was a menu.lst I could just delete what I didn't want to see at boot up. I'm just saying that it seems like they've created more problems than they've solved.

---

### Post by oldfred on 2010-09-10
I really do not see much difference in copying over the 7.04 & XP settings to 40_custom as they will not change and turning off the osprober. It then is just like editing menu.lst.

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

