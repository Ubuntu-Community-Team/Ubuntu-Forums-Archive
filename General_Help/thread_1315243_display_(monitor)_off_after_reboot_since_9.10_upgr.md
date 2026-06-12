---
title: "display (monitor) off after reboot since 9.10 upgrade"
date: 2009-11-05
forum: General Help
---

### Post by Irishpolyglot on 2009-11-05
This random problem has affected me since upgrading to Karmic. Whenever I turn my computer back on after turning it off, or after some reboots, the screen is just off. I'm on a Dell XPS M1730 laptop. It doesn't even show the initial Dell screen before the Ubuntu logo. It boots up normally (as far as I can tell).
If I keep turning it off and on again then eventually the screen will come back. It's completely random! Other than never turn off the computer again, any ideas??

---

### Post by Muhammad Ahmed on 2009-11-05
this is most likely a hardware fault,

---

### Post by Muhammad Ahmed on 2009-11-05
try rsetting your bios settings

---

### Post by Irishpolyglot on 2009-11-05
@Muhammad A hardware fault that just happened to appear exactly after I did a major OS upgrade?

---

### Post by Irishpolyglot on 2009-12-04
I still have this issue :(
I've found that after a disk scan is automatically forced after the set number of reboots, then the boot just after that things will work again! The scan seems to correct some problem, but that problem will reappear as soon as I turn it off again.
If it's a hardware issue, then I still find it curious that it appeared just after I installed Karmic and on a 6 month old high quality computer.
If it's a BIOS issue, I'd appreciate suggestions on how to fix it.

Otherwise, to at least save me a little time, can you tell me how to force a scan on the next boot? I keep having to turn the PC off and on until I get a scan forced and I'm sure that isn't doing the computer any good. How can I force a scan on EVERY boot up by default??

Why would a scan be solving the problem? And why does it come back?
I also cannot wake up after sleeping/hibernating and I'm sure it's due to the same issue. Other than keeping my computer on all the time (not possible since I travel with it every few weeks), I'd appreciate some way around this...

---

### Post by Snow986 on 2009-12-04
I don't think forcing a scan on every boot is a good idea ( for one thing, boots would take forever).  Try running a disk check with fsck. Use 'man fsck' to look up how to use it.  It could be a problem from the install that something is corrupt in the new partition or it could be a bios problem.  Can we have more details on your install, such as partitions etc.

---

### Post by Irishpolyglot on 2009-12-05
Thanks for your response. 

You are right that forcing a scan really slows things down (about 30 minutes on my system), but NOT forcing a scan in my current situation requires an extra 30 minutes of switching on and off a large number of times until I finally see the hard-drive light stay on to show that the scan is occurring (since I can't see it on the screen). After that 30 minutes, on the next reboot the screen works again. This is why I would like to just always force a scan until I solve this issue; halfing my boot-time...


I ran a system scan from the recovery CD (since the problem occurs immediately after I turn on my computer, I can't even view the monitor for accessing the recovery CD until I go through the 30 minutes rebooting + 30 minutes scanning sequence) that claims to fix problems, but that didn't help. 

I couldn't run fsck from recovery mode (accessed from grub) without ignoring the warning that the drive is mounted and I got a permissions error from within the LiveCD for trying fsck on the partition. Would that fsck find and correct errors that the e2fsck (the default used in GParted from the Live CD) I ran wouldn't? If so, how can I run it without mounting the drive, or without getting the permissions error from the LiveCD?

I'm on a 400GB **ext3** partition. Let me know how to find any other info that may help discover the issue!
Thanks so much!! An hour per boot is driving me crazy...

---

### Post by Snow986 on 2009-12-05
Can you tell me what program is doing the scanning? Such as is it a forced check from ubuntu or from something else.  Are you running any other OS's.  Do you have a swap partition?  You said you upgraded... It is possible (but unlikely) that when you upgraded that there was a corruption of some of your filesystem.  Could you try booting to the Ubuntu live cd and running a fsck and seeing what the output of the SMART tools are.  I believe that you might have to sudo apt-get smartmontools or something to that affect.  If both of those come back clean (or even before if you're desperate) it might be better to just boot into ubuntu however works for you, then get all your info off, then fresh install.  The fact that a scan "fixes" the issue really makes me think it is a file system corruption or node problem.

---

### Post by Irishpolyglot on 2009-12-09
> **Snow986 said:**
> Can you tell me what program is doing the scanning? Such as is it a forced check from ubuntu or from something else.  Are you running any other OS's.  Do you have a swap partition?  You said you upgraded... It is possible (but unlikely) that when you upgraded that there was a corruption of some of your filesystem.  Could you try booting to the Ubuntu live cd and running a fsck and seeing what the output of the SMART tools are.  I believe that you might have to sudo apt-get smartmontools or something to that affect.  If both of those come back clean (or even before if you're desperate) it might be better to just boot into ubuntu however works for you, then get all your info off, then fresh install.  The fact that a scan "fixes" the issue really makes me think it is a file system corruption or node problem.

It's GParted "doing" the scanning, but I can see from the command line that it's actually running e2fsck. I don't know what scan is forced by Ubuntu - it would be the same one as for anyone else on Ubuntu after 15 or so reboots I presume.
When I tried to run fsck it gave me a permission error when I tried to run it on the main partition. Can you suggest a way around this?
I'd really prefer not to back up and start all over again since I might just end up with the same problem.

I could still do with a temporary solution of forcing a scan on every boot. Or if anyone else has an idea of what I can do manually to eliminate this problem, please suggest...

---

### Post by Snow986 on 2009-12-09
You should probably run the fsck from the live cd.  If the problem is file system corruption, the fsck should find and fix it.  I think what is happening is you have a bad sector or just corrupt files somewhere and when it scans at boot it is fixing the problem, however the files are either being written to or something is happening to corrupt them again during use.  Then if you dont scan and "fix" the errors when you boot, you are not able to boot.  Seeing the results of fsck will help see whats going on.

---

### Post by Agent_AL on 2009-12-10
Here is my story.
Decided to make clean install of 9.10 over 9.04. Operating HP nx6125 notebook. Well, all I got were only negative conclusions.


[LIST=1]
[*]    First of all, **OP's problem** on my system: shortly after boot splash there's a nice chance to have screen going off (even LCD lamps are not working) permanently while computer continues to load OS. Trying to hit lid button doesn't do a thing and I'm being forced to restart in hope that next boot will be ok. Usually, first boot after turning on computer goes ok and after boot splash monitor does turn off together with screen backlight however shortly in 2 seconds turns back on.
[*]    Boot time is enormously higher than in previous version. In 9.04 process from grub initialization to completely functional gnome interface took about minute or so. Now with 9.10 it takes at least twice longer what is unacceptable. No clues what's the reason for that.
[*]    Annoying GRUB menu shows up with options what to do before boot. In 9.04 I had to push special button to invoke that menu which was much more convenient. But that's not the problem. After selecting item in that menu it keeps displaying for 20 seconds with no progress and reaction on user input.
[/LIST]
 
I'm fed up with that. Many users have said that before about 9.10 and I will say that once more: 9.10 is a **major step back** in terms of UI and boot sequence design.
I could bear this version only if awful boot sequence and UI was the only issue, but that severe screen problem just makes me mad.

Some people say it's corruption or NVidia video card drivers related problem. Well, surprise! I have an ATI card with fglrx drivers and this problem occurs completely on random leaving no error logs behind and fsck gives nothing. I guess this issue will be hard to narrow nevertheless there's a plenty of users reporting about it. All is known about:


[LIST=1]
[*]    it happens only on notebooks
[*]    only on 9.10
[*]    not just after boot, but each time monitor turns off (after notebook lid closing, for instance, there's a nice chance to get your system running without monitor operating).
[/LIST]
 

I'm wiping this thing out of my drive in favor of 9.04 until next version available. Hopefully, 10.04 I'll get old booting sequence with INFORMATIVE progress bar and no additional splashes like that tiny buntu icon after which my monitor goes off for ever. If no, well guess I'll stick to win7 like I always did.
Sorry for that shitstorm, but I'm feeling pretty anxious when my second favorite system makes such degradations for no particular reason.

---

### Post by Snow986 on 2009-12-10
It looks like your problem could be the same as the OP's.  Does a forced scan on boot "fix" the problem?  If it were me, I would just stick with 9.04 until 10.04. Its too bad there are lots of these issues popping up.

---

### Post by Irishpolyglot on 2009-12-14
Wow, I'm somewhat relieved to see others are having this issue. I thought I was having a hardware problem. Sorry for my ignorance, but what is OP?

So, I am definitely in a frustrating situation. My options seem to be a) reinstall 9.04, get rid of the monitor issue, BUT get back to the random freeze issue that I wasted many many days trying to solve to no avail, which was solved in 9.10 or
b) Live with this issue and hope that 10.04 solves it
c) Abandon Ubuntu since no amount of tweaking ever seems to give me a stable system, despite trying for 2 years on different computers...

Reinstalling 9.04 isn't an option for me. The 1 hour boot up time because of all the reboots and the scan are actually much less annoying than the random freezes believe it or not.

In case someone does find a non-re-install solution, can you point me to other threads about this issue? I searched but didn't find, the keywords I'm using must be off.

I've stuck with Ubuntu this long and I'm determined to reach a stable system. In the mean time **can someone please tell me how to force a scan on every boot?** The current situation has me wasting an extra half an hour with reboots before the scan solves the issue.

I will try to do an fsck from the live CD (would that be any different to an e2fsck)? But I'm only doing that after I find out how to force a scan - surely there's a configuration file I can gedit to change the number of boots to count from whatever number it is now to 1? :) I heard it's 15, but I definitely have to reboot more than 15 times to see the forced scan (hence 30 minutes until scan..)

Thanks for any help!

---

### Post by Snow986 on 2009-12-14
Go ahead and try the live cd and see what happens.  I'm not sure what the difference is from e2fsck.  OP stands for Original Poster or you. Good luck!

---

### Post by Irishpolyglot on 2009-12-24
This issue has been solved. It was hardware in the end. I believe the constant freezing (a common issue among 9.04 users with similar hardware to mine) for 6 months must have burnt my video card and thus given me the new issue when the old one had been resolved when I upgraded to 9.10.

Luckily it was still under warranty so they replaced my entire video card and now things are working fine. Thanks for all the advice!

---

### Post by Agent_AL on 2009-12-29
Guess it's quite abnormal that operating system is destroying hardware. :(
It could be 300$ worth video card and warranty might become void just because that hardware piece was recommended for use with Windows only.

I had an issue with 8.04 when I had to replace my entire hard drive (luckily warranty was still active). I was running Windows XP on two months old hard disk and once I decided to try out ubuntu and installed it using wuby. As result I got completely new drive head malfunction and dozens of bad sectors on that volume which didn't go away after several deep formatting procedures. Right after that day drive started to act weird and produced new bad blocks time to time (clicking sound occurred and OS froze = congrats you have a new block!). One day I got severe data loss causing both OSes on that drive unbootable and decided to backup while there's a chance to save some ****. 

Since that moment I will never install linux again on my home machine. Hardware is too expensive to spare just like that. Who knows, maybe hard drive was initially defective but I have no idea why the problem appeared exactly after ubuntu installation. Drive was in hard use for two months and I wouldn't say that just installation/reformatting process was the cause for head malfunction.
Maybe I'm just unlucky person to be with lunix, but that's my life experience.

---

