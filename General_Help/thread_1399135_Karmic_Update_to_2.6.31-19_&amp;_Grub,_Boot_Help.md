---
title: "Karmic Update to 2.6.31-19 &amp; Grub, Boot Help"
date: 2010-02-05
forum: General Help
---

### Post by shadetree1 on 2010-02-05
Hi, I am a recent Ubuntu user multi booting Ubuntu and M$.  My 4 PC's are always on and updated from upstream.  I attempted to reboot and issues raised.
 
2 PC's having Ubuntu on there own drives will not boot any menu list entry now (bricked).  and 2 PC's having Ubuntu on a shared drive will not boot M$ entry.
 
As stated, I am new and wonder if there is a way to update Grub with a live disk to revert or fix the Grub configs?
 
Thank you for any advise.

---

### Post by shadetree1 on 2010-02-05
On the single HDD PC's, Ubuntu boots but selecting M$ displays, "error: Invalid Signature."  

The multi HDD PC's don't boot at all!  When selecting Ubuntu this displays, "Loading initial Ram Disk......error: File not found."  Selecting M$ displays, "error: invalid file name `+'. 

update-grub2 changes nothing.

---

### Post by SaintDanBert on 2010-02-05
Since you mention Karmic, I'm sure that you remember that GRUB-2 is at work instead of GRUB-1(legacy). I suspect that whatever your configuration, this automagic processing stumbled and fouled your ability to boot.

I recommend booting from a live-CD like SystemRescueCD [ http://www.sysresccd.org/ ]( http://www.sysresccd.org/ ) or your Karmic distro to see what is there. I would poke around to see what files exist and if their contents make sense for GRUB-2. Consider running [highlight] update-grub2 [/highlight] again manually to watch for errors.

During software installs, [highlight] update-grub2 [/highlight] or similar runs. It searches and discovers available boot targets, chews on settings from ** /etc/default/grub ** and creates the new ** /boot/grub/grub.cfg **.
[indent]
[highlight] 
Do not edit ** /boot/grub/grub.cfg ** by hand!
[/highlight]
[/indent]

---

### Post by Kir_B on 2010-02-05
Funny that I should run into this, as I've just experienced a similiar problem. Luckily for me I had 4 kernels to choose from in recovery mode and the oldest one worked. I went into recovery mode and ran the update grub command and then rebooted successfully. Just hang on for a couple of minutes and I'll dig up the link to my thread that got me out of a similiar bind a while back. Hang tight.

   Peace. Kir_b

---

### Post by Kir_B on 2010-02-05
I don't know what level of expertise you have but here is the link to the beginning of the thread: [COLOR=#cc33cc][my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")

Depending on your expertise level, at least skip ahead to the directions given by "lmarmisa". He really saved my bacon. Now as was pointed out, Ubuntu Karnic Koala is using grub2, but if you've upgraded to Karmic from Jaunty and did not manually upgrade your grub legacy to grub2, you'll still be using the old grub and the instructions from my previous thread will, unfortunately  do you absolutely no good and _may_ actually make things worse. I'm definitely NOT an expert, so get further advice if needed.

Good luck and hope your day gets better real soon. Kir_b
[/COLOR]

---

### Post by Cerox Rex on 2010-02-05
This kernel update broke my grub too, now i just get "Error: File not found" and get thrown into a scary Grub-rescue shell wich i cant make heads or tails of!

---

### Post by Kir_B on 2010-02-05
> **Cerox Rex said:**
> This kernel update broke my grub too, now i just get "Error: File not found" and get thrown into a scary Grub-rescue shell wich i cant make heads or tails of!

Just follow, to the letter, the instructions given by "lmarmisa"
in the "[COLOR=#cc33cc][my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR]" and trust me everything will work out fine. I was freaking right out when it happened to me to. Good luck. Kir_b

---

### Post by Cerox Rex on 2010-02-05
> **Kir_B said:**
> Just follow, to the letter, the instructions given by "lmarmisa"
in the "[COLOR=#cc33cc][my grub2 nightmare won't end]("http://ubuntuforums.org/showthread.php?t=1325901")[/COLOR]" and trust me everything will work out fine. I was freaking right out when it happened to me to. Good luck. Kir_b


Thnx, this worked out great. 

Hope no more kernel updates will break my grub again! Kinda anoying :P hehe

---

### Post by shadetree1 on 2010-02-05
Thanks for the info. 
 
I have fresh installs running the maintainer's Grub-pc.
 
I will check out the link when I get home tonight.
 
Again, Thank You :D
 
PS.  None of the older kernels 9.4 or 8.4 on other partitions or drives will boot either and showing the same errors!

---

### Post by Kir_B on 2010-02-05
> **shadetree1 said:**
> Thanks for the info. 
 
I have fresh installs running the maintainer's Grub-pc.
 
I will check out the link when I get home tonight.
 
Again, Thank You :D
 
PS.  None of the older kernels 9.4 or 8.4 on other partitions or drives will boot either and showing the same errors!

I think all that needs to be done is to run the "sudo update-grub2" command and everything, including your spysoft, should then be recognised by the grub2. Remember that if you upgraded to Karmic from Jaunty and then didn't manually upgrade your grub, you'd still be running grub legacy, which means it's a different command to update the grub. I do believe the command for updating grub legacy is: sudo update-grub .

                       Good luck. Kir_b

---

### Post by LoREZ on 2010-02-08
I got an "invalid signature" on selecting my Win 7 install.  This occurred after the *31-19 update for for the kernel.  It also dropped my menu style, defaulting back to the original.  None of the above suggestions helped me, but I found an answer.

First, when I tried to run "sudo update-grub2"  I would get an error similar to this:

```
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
```

So I went [[COLOR="Blue"]here[/COLOR]]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install") to find out what a "device.map" was and how I could manipulate it.  After some searching, came across this gem:

```
sudo grub-mkdevicemap
```

Funny how this command is said to have little significance for users.  After you execute it, force grub to read and save the new device.map:

```
sudo update-grub2
```

That should do it, if the update caused the problem.  Just remember, my error specifically mentioned device.map, so this may not work for everyone.

You know, recommended updates shouldn't threaten to brick your machine.  What if I were running a business out of this box? (yeah, "backup," but time=money, no?)

---

### Post by shadetree1 on 2010-02-08
> **LoREZ said:**
> I got an "invalid signature" on selecting my Win 7 install.  This occurred after the *31-19 update for for the kernel.  It also dropped my menu style, defaulting back to the original.  None of the above suggestions helped me, but I found an answer.

First, when I tried to run "sudo update-grub2"  I would get an error similar to this:

```
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
```So I went [[COLOR=Blue]here[/COLOR]]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-install") to find out what a "device.map" was and how I could manipulate it.  After some searching, came across this gem:

```
sudo grub-mkdevicemap
```Funny how this command is said to have little significance for users.  After you execute it, force grub to read and save the new device.map:

```
sudo update-grub2
```That should do it, if the update caused the problem.  Just remember, my error specifically mentioned device.map, so this may not work for everyone.

You know, recommended updates shouldn't threaten to brick your machine.  What if I were running a business out of this box? (yeah, "backup," but time=money, no?)

OMG,  LoREZ this worked on both my single HDD PC's THANK YOU VERY MUCH! 

My other two multi HDD PC's only go to grub> when a OS is selected, not able load a kernel run a terminal to repair.  Later I will try to have Grub it's self map and update.

Thanks again!

---

### Post by shadetree1 on 2010-02-08
Well none of the commands are recognized in grub> that fixed the other PC's in a terminal.  I need to be in a kernel root to use a terminal.  

I'll try the other suggestions listed.

---

### Post by LoREZ on 2010-02-09
Glad I was able to help.  I hope it works out for you.  Meanwhile, I would definitely study that link I posted.  If you read it closely, there are a large number of possible angles of attack on grub2 problems, but you have to be creative sometimes.  I wasn't even sure the [FONT="Courier New"]grub-mkdevicemap[/FONT] command would work by itself when I first tried it.  The guy who runs the site seems to put a lot of stock in this command, though:

```
sudo grub-install /dev/sda
```

Replace "sda" with the device where you've got grub2 installed.  

This didn't work for me, but the site admin over there has the most comprehensive knowledgebase on grub/grub2 I know about, and he believes in that command for most problems.  The key to why that might work is that grub2 is mostly automated, and should see where everything is and how to put it all together during its probe operation. Still, obviously it is not flawless automation, or neither of us would have had trouble...

---

### Post by shadetree1 on 2010-02-11
> **LoREZ said:**
> Glad I was able to help. I hope it works out for you. Meanwhile, I would definitely study that link I posted. If you read it closely, there are a large number of possible angles of attack on grub2 problems, but you have to be creative sometimes. I wasn't even sure the [FONT=Courier New]grub-mkdevicemap[/FONT] command would work by itself when I first tried it. The guy who runs the site seems to put a lot of stock in this command, though:
 
```
sudo grub-install /dev/sda
```
 
Replace "sda" with the device where you've got grub2 installed. 
 
This didn't work for me, but the site admin over there has the most comprehensive knowledgebase on grub/grub2 I know about, and he believes in that command for most problems. The key to why that might work is that grub2 is mostly automated, and should see where everything is and how to put it all together during its probe operation. Still, obviously it is not flawless automation, or neither of us would have had trouble...
 
A family emergency took priority over my attempt to repair Grub on the multi drive PC's.  Nether will go to a kernel to use a terminal command.  I will reinstall Grub tonight I hope!
 
Thank you for the help.

---

### Post by shadetree1 on 2010-02-12
The multi drive PC's are up and running now.  I found the best way for me with grub-pc was to boot with a M$ disk and fix MBR, then boot to Ubunu with Super grub2 and chose the latest kernel and uninstalled their grub's.  
 
I repeated this to the other kernel versions partitions 9.04 and 8.04.  I rebooted and of course went to M$ on both PC's :p.  Then I booted with Super grub2 and went to the latest Karmic kernel-19 and installed the maintainers grub-pc and all is well :D.
 
Wow, that was a experience.  I am less than a year in to Ubuntu and have learned much with upgrading? to 9.10.  I hope 10.4 will be smooth as my introduction to Ubuntu with 8.04 on my various PC's.
 
That Super grub2 disk is a keeper, with it able to boot any system type drive and more.
 
I want to thank everyone who helped.  At first for a while, the only PC I had to use was my CaptiveWorks LMC4000.  It has Gentoo, my first introduction to Linux.  That is another chapter in my book of learning ;).
 
Now I need to read how to mark this thread (Solved)............. 
 
shadetree

---

### Post by Kir_B on 2010-11-21
> **shadetree1 said:**
> 
 
Now I need to read how to mark this thread (Solved)............. 
 
shadetree

Hey shadetree1.

I'm really glad to hear that you got that worked out.

I've currently got my own system that's been bricked now for the last three months (I got really sick and tired of trying things that refused to work for me and so I've been running an old backup that I'm absolutely terrified to update).

Thanks for the [Super grub2 Disk]("http://www.supergrubdisk.org/category/download/supergrub2diskdownload/") information. It may be helpful with my problem, and even if it isn't, it'll most likely be helpful down the road.

Anyhow, one way to mark this thread as "solved", is to go to your _first_ post in the thread, click on the "Edit" button, and then put Solved in brackets at the start of the title (I usually see it done with the square brackets. ie. [Solved]). Now click the "Preview Post" button under the editor box to make sure it worked alright and if it did, click the "Submit Reply" button and this thread will most likely help many others. (I know I was overly descriptive, but I did it that way so some of the greener newbies may benefit from it)

Good day. Kirby ):P

P.S. Sorry it took so long to get back to you, but for whatever reason, I wasn't subscribed to this thread.

**EDIT: **I just noticed that you figured out how to mark the thread solved. I guess I'm used to seeing the solved in the title of each post. Don't I feel like an idiot!!![B] LOL :oops:
[/B]

---

### Post by shadetree1 on 2010-11-22
Hello Kirby,  I hope everything is fine now up there.
 
I'm at 10.4 and starying....no more version upgrades for me until this release is at it's EOL.
 
I wiped all versions of Linux but this and Win7 and am using a server on my LAN to keep both OS's up to date on all my PC"s.
 
Well better get to work...ttyl :)

---

