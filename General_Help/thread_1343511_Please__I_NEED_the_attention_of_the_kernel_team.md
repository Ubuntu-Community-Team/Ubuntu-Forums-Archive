---
title: "Please  I NEED the attention of the kernel team"
date: 2009-12-01
forum: General Help
---

### Post by jcobban on 2009-12-01
I do not understand why I cannot get the attention of the kernel team.  Karmic Koala is freezing on me **several times a day**.  I am bending over backwards to provide documentation.  I am willing to run any test that is suggested, but I just cannot get any response from the developers.

Once again I am posting this message from **MICROSOFT VISTA** because my Ubuntu system has frozen **again!**

I cannot continue using Ubuntu without a resolution of this problem.

I have reported the problem through Apport but have received no acknowledgement.  I believe that the problem is probably specific to the Intel 845GV chipset on my motherboard, but that chipset is deployed in millions of computers.  I have even considered replacing my motherboard, but all of the new motherboards take SATA drives, so I would have to replace the whole bloody system and copy all of my data over to resolve the problem through a hardware fix, so it is not just a few hundred dollars, it is also much of a day of lost productivity.  And although the cost for me to implement that hardware fix would probably be less than the cost to the development team to figure out what is wrong in the kernel driver for that chipset and fix it, they would be left with a buggy kernel which would inflict this problem on the next person to try using a computer with an 845 chipset, and they would have lost my cooperation in debugging the problem.

Please.  I am trying not to lose my temper, but if I cannot get a resolution soon I may start behaving in an intemperate and unproductive way.

---

### Post by MelDJ on 2009-12-01
so you can boot and after a while it freezes?

---

### Post by dcstar on 2009-12-01
> **jcobban said:**
> I do not understand why I cannot get the attention of the kernel team.  Karmic Koala is freezing on me **several times a day**.  I am bending over backwards to provide documentation.  I am willing to run any test that is suggested, but I just cannot get any response from the developers.


Really, what is the Launchpad bug number that you have created?

It is totally pointless posting such things here, as this is a forum of Ubuntu **users** trying to help other Ubuntu **users**.

---

### Post by ed-koala on 2009-12-01
Does this thread shed any light on the issue?

[http://ubuntuforums.org/showthread.php?t=1027080]("http://ubuntuforums.org/showthread.php?t=1027080")

---

### Post by jcobban on 2009-12-03
> **MelDJ said:**
> so you can boot and after a while it freezes?

Yes.

---

### Post by jcobban on 2009-12-03
> **dcstar said:**
> Really, what is the Launchpad bug number that you have created?

It is totally pointless posting such things here, as this is a forum of Ubuntu **users** trying to help other Ubuntu **users**.

Launchpad number 477918

If this is an pointless place to post then tell me where I should report this.  I have posted it to launchpad and that has been a waste of time.  I NEED to get the attention of the team responsible for the kernel, but I cannot see any such information either here or at linux.org!

---

### Post by jcobban on 2009-12-03
> **ed-koala said:**
> Does this thread shed any light on the issue?

[http://ubuntuforums.org/showthread.php?t=1027080]("http://ubuntuforums.org/showthread.php?t=1027080")

No.  The problem did not occur until after I installed Karmic Koala so the problem is introduced kernel 2.6.31.  The problem also occurs whether or not I specify nomodeset in the boot.

---

### Post by MaxIBoy on 2009-12-03
Here's something to try. Install a different distro like Debian or Fedora to see if the problem goes away.

What is the kernel you are currently using, what is the hardware you have, more specifically? Could you crosslink to some of your other old threads so we can see some of the things you have already tried? Has this persisted across kernel updates or distro upgrades?


But try a different distro, it may like your hardware better.


EDIT: that fix Wojox posted looks promising. In which case, the bug is in Xorg, not the kernel.

---

### Post by doas777 on 2009-12-03
well, if it is a kernel bug, then it isn;t ubuntu people you need to talk to. they do customize it a little, but that is about it. 

if you want to file a bug report with the linux foundation, you first need to install the vanilla mainstream kernel. they will not accept bug reports against the ubuntu kernel.

just a hint, the problem is not likely the chipset version, since, as you point out, that would have been a showstopper no one could have missed.

when my box starts doing  bizarre things, and a rebuild does not fix them, then I usually buy a new mobo. a single blown cap, can really mess up a board. if that fails then i know for sure that the cause is in something I did.

---

### Post by wojox on 2009-12-03
[This guy/girl fixed it.]("http://www.ubuntudiary.co.cc/2009/05/xorgconf-finally-solved-for-intel-845.html")

---

### Post by jcobban on 2009-12-03
> **MaxIBoy said:**
> Here's something to try. Install a different distro like Debian or Fedora to see if the problem goes away.

What is the kernel you are currently using, what is the hardware you have?

Thank you for the suggestion of another distro, as that could help to verify my conclusion that the problem is in the kernel.  However even if another distro worked it would not resolve my problem, which is to be able to run on Ubuntu.  Furthermore it would not address the need to fix the bug that is causing the freeze.  The bug will never be fixed if the development team doesn't look at the problem.

I am currently running with kernel 2.6.31-15 but I have had the problem ever since installing Karmic, which was several kernels ago.  I did not have the problem with Jaunty or any previous release.  The problem occurs whether or not I boot with nomodeset.  As I said in the original post I am running an Intel PC with the 845GV chip set.  I tried booting with the last Jaunty kernel, and while my system does not freeze with that kernel there appears to be some incompatibility between that old kernel and the higher levels of Karmic that makes the system non-functional.

I do not understand why I have to keep repeating this litany.  I am **not** asking the participants in this forum to resolve this problem.  As has been pointed out to me over and over this is a user forum.  The only people who can help me are the members of the **kernel development team**.  The only thing I am asking is how to get in touch with them to raise the priority of this problem, since there has been no response to my launchpad report.

I am sorry if I come across as petulant, but I am really tired of having my system freeze, and being unable to obtain support.

---

### Post by jcobban on 2009-12-03
> **wojox said:**
> [This guy/girl fixed it.]("http://www.ubuntudiary.co.cc/2009/05/xorgconf-finally-solved-for-intel-845.html")

That was a problem in kernel 2.6.26 that was fixed by going to 2.6.27.  I am having a problem at 2.6.31.

---

### Post by MaxIBoy on 2009-12-03
We're capable of fixing more issues than you're giving us credit for... ;)

That fix posted by wojox looks worth a try.

Have you tried running it in textmode and seeing if it crashes that way?

EDIT: Try SSHing in from another computer and forwarding X over SSH, using an X server without rendering it on the computer's actual screen but instead sending the image over the SSH connection.


> **jcobban said:**
> That was a problem in kernel 2.6.26 that was  fixed by going to 2.6.27.  I am having a problem at 2.6.31.
Did you actually read it?! He only recommends the kernel upgrade as an aside, and goes on to talk about configuring xorg.conf.

---

### Post by wojox on 2009-12-03
Maybe it still needs tweaking. [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582). Does you xorg.conf look good ?

---

### Post by jcobban on 2009-12-03
> **doas777 said:**
> when my box starts doing  bizarre things, and a rebuild does not fix them, then I usually buy a new mobo. a single blown cap, can really mess up a board. if that fails then i know for sure that the cause is in something I did.

I am not a Linux guru.  I have no idea how to go about installing a kernel.

The problem is not something specific to my particular computer because Jaunty works fine, and so does WinXP.

The 845GV chipset is rather old, so there may not be many people with that chipset who have already moved to Karmic.

---

### Post by doas777 on 2009-12-03
> **jcobban said:**
> I am not a Linux guru.  I have no idea how to go about installing a kernel.

The problem is not something specific to my particular computer because Jaunty works fine, and so does WinXP.

The 845GV chipset is rather old, so there may not be many people with that chipset who have already moved to Karmic.

last year, my xp box started crashing during rdp sessions. I spent months trying to figure it out, but in the end, buying a new mobo was the correct answer. now ask yourself, what set of circumstances would lead to only that one app causing an eventual set of circumstances where the mobo caused a lock followed by a bsod?

---

### Post by MaxIBoy on 2009-12-03
Try verifying that another distro with a 2.6.31 or newer kernel (Fedora 12) has similar issues. If it does not have issues, then maybe you've found the distro for you. :) But also if it does not have those problems, then that narrows down where the bug is.

---

### Post by hoppipolla on 2009-12-03
erm... calm down man it's only a computer!

If you have to use Vista you have to use Vista, we can't always get things to work right away!

Ok now I'm gonna re-read and attempt to answer this! lol :)


Right... I have actually never seen a problem like this before, the first thing I thought when you said it freezes was hardware failure or overheating, as these kinds of things are very uncommon on Linux at least in my recent experience with good kernels.

Maybe try some of the fixes people posted here, or worst comes to the worst buy a compatible motherboard off ebay, you don't need to buy a brand new one just get it from a reputable seller :)

You'll be fine with the info in this thread, and dude if you have to use Vista or Windows 7 or something it's not the end of the world - I dual boot anyway! :)

---

### Post by Raffles10 on 2009-12-03
Am I being dumb or something.......if the problem exists with karmic but not with jaunty doesn't the solution seem obvious. Is there some showstopper reason why you can't downgrade ? Upgrading to the latest release isn't compulsory, lots of people still run older ubuntu's 'cause they work great for them.

---

### Post by jcobban on 2009-12-03
> **MaxIBoy said:**
> We're capable of fixing more issues than you're giving us credit for... ;)

That fix posted by wojox looks worth a try.

Have you tried running it in textmode and seeing if it crashes that way?

EDIT: Try SSHing in from another computer and forwarding X over SSH, using an X server without rendering it on the computer's actual screen but instead sending the image over the SSH connection.



Did you actually read it?! He only recommends the kernel upgrade as an aside, and goes on to talk about configuring xorg.conf.

[LIST=1]
[*]The problem discussed by that fix was a performance problem, particularly with refresh.  I believe that I actually did see that problem with the appropriate releases although it only manifested itself when I did a manual suspend/resume.  As I understand it TPTB decided to resolve the performance problem by a feature called KMS: "kernel mode set".  certainly KMS, as defaulted in Karmic, does resolve that performance problem in the situation where I encountered it.  I have not observed any of the issues described by the original problem statement while running with KMS, although they do return if I specify "nomodeset" to GRUB.
[*]I am not encountering a performance problem, I am encountering a complete solid freeze of the UI.  The display is frozen except that the cursor follows mouse movements, and inputs through the mouse and keyboard are ignored.  So for example I cannot deliver a keyboard ctl-S command to my open OOo document to save it, so all my recent work is lost when I reboot.  All processes are apparently running fine except that I cannot communicate with them except if they have some network connection.  For example my Apache server still responds normally.
[*]I do not understand what you mean by "running it in textmode".  In any event as I have explained this is not a crash, it is a freeze.
[*]My system did not freeze on Hardy.  My system did not freeze on Intrepid.  My system did not freeze on Jaunty.  It **consistently** freezes on Karmic!
[*]I only have one system running Linux.  My only other system is a laptop running Vista.  I suppose I could change the laptop to a dual-boot configuration so I could try running an X server remotely.
[/LIST]

---

### Post by jcobban on 2009-12-03
> **hoppipolla said:**
> erm... calm down man it's only a computer!

If you have to use Vista you have to use Vista, we can't always get things to work right away!


The computer doesn't freeze, only the UI of the operating system.  I am not upset with the computer, I am upset with the fact that a brand new release of Ubuntu is put out with so much hoopla, and I cannot get the attention of the people responsible for the new release when I am forced to reboot it every couple of hours.

Neither Vista nor Win7 will run on a computer with the 845GV chipset.  I do run WinXP on it.

Yes I have to run some apps on Vista, but other critical apps only run on Linux.

---

### Post by doas777 on 2009-12-03
um, you do know that no one at ubuntu has too much to do with the kernel, right?

---

### Post by michaelzap on 2009-12-03
Check the link in my signature below. I had the same issue as you did when I installed Karmic, and it was bad enough to force me to use Vista also. I fixed it by using the Lucid RC kernel, which is as easy as downloading three .deb files, doubleclicking on them, and restarting.

---

### Post by jcobban on 2009-12-03
> **MaxIBoy said:**
> Try verifying that another distro with a 2.6.31 or newer kernel (Fedora 12) has similar issues. If it does not have issues, then maybe you've found the distro for you.

I tried Fedora before moving to Ubuntu.  I just couldn't get it to do what I wanted.  In particular a number of features that I felt were essential to my system were part of the extra-cost commercial version of Fedora, for example support for NTFS.  My system dual boots Windows and Linux, and the only reliable file system that can be shared is NTFS.

---

### Post by michaelzap on 2009-12-03
You'll likely have the same instability/kernel freezing with any distro that uses the 2.6.31 kernel - it's a big FAIL on my hardware anyway.

---

### Post by jcobban on 2009-12-03
> **michaelzap said:**
> Check the link in my signature below. I had the same issue as you did when I installed Karmic, and it was bad enough to force me to use Vista also. I fixed it by using the Lucid RC kernel, which is as easy as downloading three .deb files, doubleclicking on them, and restarting.

I have never installed a kernel that did not come as a regular update.  Your description of the process is too vague for me to follow:
[LIST=1]
[*]Download which .deb s?
[*]From where?  What is "Lucid".
[/LIST]

---

### Post by michaelzap on 2009-12-03
> **jcobban said:**
> I have never installed a kernel that did not come as a regular update.  Your description of the process is too vague for me to follow:
[LIST=1]
[*]Download which .deb s?
[*]From where?  What is "Lucid".
[/LIST]

Sounds like you didn't click on the link in my signature and read through that thread, but that's OK I guess.

Lucid is the next Ubuntu release, which is currently in development. It will use a later version of the Linux kernel. The version that shipped with Karmic has way too many bugs and regressions; in my opinion they shouldn't have released Karmic with that kernel at all.

You can get the latest mainline kernel files here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)

Download the linux-headers...all.deb file as well as the linux-headers...amd64.deb and linux-image...amd64.deb files (unless you are running 32-bit Ubuntu, in which case download the i386 versions of those two files instead). You do not need the source file.

Doubleclick on each of the files to run them with the package manager. If you get any unmet dependencies errors, that just means that you need to install one of the other files first (so just install the next one and then come back to the one that gave you an error). After you've installed all three files, restart your computer.

In the grub startup menu you should now see the new kernel at the top of the list (it should be the default). Boot up your computer using that kernel and see how it goes. In my case the difference was night and day (with the old kernel Karmic was unusable; with this one it works better than Jaunty).

If for some reason this doesn't help or you don't like it, just reboot your computer and choose the older kernel at grub. It won't affect your system to leave the new kernel installed, but you can remove it using Synaptic. The only issue that I've seen that would cause you not to be able to use this kernel would be if you get errors installing the kernel (not dependency errors, but errors once it starts to install), which could mean that you have hardware that requires a driver not included in this mainline kernel.

---

### Post by fluffman86 on 2009-12-03
are you certain this is actually a kernel issue?  I've read through the whole thread and haven't seen any evidence other than the fact you're using karmic.  If the UI is freezing, but the mouse is moving, then the computer is *NOT* frozen, at least not the kernel, anyway.  Try pressing CTRL + ALT + F1 to get to a command line.  If you can log in there, run "sudo killall -9 Xorg" and then "sudo /etc/init.d/gdm restart"

Also try typing "ls" and navigate around your system some with "cd foldername"  If you can do anything at all from the command line, then the kernel isn't frozen.

---

### Post by michaelzap on 2009-12-03
> **fluffman86 said:**
> are you certain this is actually a kernel issue?  I've read through the whole thread and haven't seen any evidence other than the fact you're using karmic.  If the UI is freezing, but the mouse is moving, then the computer is *NOT* frozen, at least not the kernel, anyway.  Try pressing CTRL + ALT + F1 to get to a command line.  If you can log in there, run "sudo killall -9 Xorg" and then "sudo /etc/init.d/gdm restart"


I agree that's kind of strange behavior for a kernel freeze, but things like that happened to me before I upgraded to the new kernel. I would get KernelOops alerts and the system would become more and more sluggish and unstable until finally only the pointer would respond. No text input worked in my case (not even REISUB), and I don't know if processes were running or not at that point since I never tried to check that from the outside.

I would also routinely get complete lockups with caps lock lights, sudden reboots, and every once in a while a logout to GDM, but I also got the mouse pointer madness just to keep things interesting.

---

### Post by MaxIBoy on 2009-12-04
Keeping in mind that the graphics drivers are part of the kernel codebase and run in kernel space, the graphics stack could crash and it would technically be a kernel bug. Or the input drivers could have crashed, or something.


If Fedora worked without freezing, keep in mind that does help narrow things down.


Try the kernel download that other guy suggested, if that doesn't resolve your problem straightaway we can look at what settings the Fedora people use with their kernels.

---

### Post by jcobban on 2009-12-05
> **fluffman86 said:**
> are you certain this is actually a kernel issue?  I've read through the whole thread and haven't seen any evidence other than the fact you're using karmic.  If the UI is freezing, but the mouse is moving, then the computer is *NOT* frozen, at least not the kernel, anyway.  Try pressing CTRL + ALT + F1 to get to a command line.  If you can log in there, run "sudo killall -9 Xorg" and then "sudo /etc/init.d/gdm restart"

Also try typing "ls" and navigate around your system some with "cd foldername"  If you can do anything at all from the command line, then the kernel isn't frozen.

The keyboard is dead, so I cannot get a command line.  I am 

I have now tried with two other kernels:  the Lucid RC kernel and the last Jaunty kernel.  The GUI still freezes, indeed it freezes more frequently with the Lucid kernel.  So you are right, the problem is not in the kernel, it is in Karmic itself, presumably in Xorg.  That is still no justification for my inability to attract the attention of the support team.

To go back to Jaunty I would have to backup the entire filesystem, reinstall Jaunty from scratch, and then reinstall all of my applications.  It seems to me it would be a week before I could get any actual **work **done.

---

### Post by jcobban on 2009-12-05
> **MaxIBoy said:**
> Keeping in mind that the graphics drivers are part of the kernel codebase and run in kernel space, the graphics stack could crash and it would technically be a kernel bug. Or the input drivers could have crashed, or something.


If Fedora worked without freezing, keep in mind that does help narrow things down.


Try the kernel download that other guy suggested, if that doesn't resolve your problem straightaway we can look at what settings the Fedora people use with their kernels.

The Lucid RC kernel fails even faster and more spectacularly than the Karmic kernels.  In some cases the screen literally flashes solid white before going to black!

Also going back to the Jaunty kernel now freezes as well.  Indeed of all of the kernels I have tried the current Karmic kernel has the longest MTBF, even if it is measured only in hours.  Since the GUI freezes regardless of the choice of kernel, and regardless of whether KMS is used, it is possible that the problem is elsewhere, but I am not a Linux guru and all I have ever asked is that somebody tell me **what documentation to collect** so this problem can be resolved for the whole community.  

I am annoyed with the Karmic support team because they cannot seem to take the time to even look at my Apport report!  I cannot imagine the drones from Redmond being so apathetic if Windows 7 users were encountering a problem this severe.  This problem is bad public relations for the Ubuntu brand name.  I spoke with the manager of a local computer shop yesterday and he had already heard of the problem and was warning his customers not to go to Karmic.  If this is not addressed PDQ this problem is going to show up in the mainstream media!

I am posting from M$ Vista because Karmic has frozen ... again!

---

### Post by blueridgedog on 2009-12-05
> **jcobban said:**
> No.  The problem did not occur until after I installed Karmic Koala so the problem is introduced kernel 2.6.31.  The problem also occurs whether or not I specify nomodeset in the boot.

Deleted as I did not see the entire thread.

---

### Post by blueridgedog on 2009-12-05
> **jcobban said:**
> 

I am annoyed with the Karmic support team because they cannot seem to take the time to even look at my Apport report!  I cannot imagine the drones from Redmond being so apathetic if Windows 7 users were encountering a problem this severe.  This problem is bad public relations for the Ubuntu brand name.  I spoke with the manager of a local computer shop yesterday and he had already heard of the problem and was warning his customers not to go to Karmic.  If this is not addressed PDQ this problem is going to show up in the mainstream media!

I am posting from M$ Vista because Karmic has frozen ... again!

Wow.  You really have a vastly different vision of what Linux is than I.  To call the volunteers working on kernel development apathetic because they have not replied to your issue seems arrogant.  

You can buy support for ubuntu if your issue is urgent: [http://www.ubuntu.com/support/services/advanced](http://www.ubuntu.com/support/services/advanced)

I wish you luck with your problem, but suspect you may have a hardware issue.  I also think you would have more luck in asking for help than in blasting those who have already given so much of their time.  Why not start a thread looking for a solution, rather than one implying that everything to do with your system is OK and the problem MUST be the kernel?

---

### Post by fluffman86 on 2009-12-05
Another thing to try...I believe you said your desktop was freezing, and you had vista on a laptop.  On your desktop:

sudo apt-get isntall openssh-server

And install putty on your vista laptop.  Boot the desktop, and SSH into it from putty.  Once in, type 'top' and you should see a clock in the top left and a command line version of System Monitor.

Now use the desktop as normal until it freezes.  When it does, look at your laptop to see if the clock is still ticking and see if any commands in particular are using a lot of memory.

If things are still running, then your kernel is still working.  If a particular command is eating a lot of CPU (like Xorg) then you can press 'q' to quit top, and then

sudo killall -9 Xorg
sudo /etc/init.d/gdm restart

and see if you get your system back that way.

---

### Post by michaelzap on 2009-12-05
> **blueridgedog said:**
> I wish you luck with your problem, but suspect you may have a hardware issue...
It kind of sounds like that to me now, too. Check your system logs to see if there's any hint of where specifically the problem is manifesting itself. You tried the final (not RC) version of the Lucid kernel, right?

You could also try a more stable Distro such as Debian Lenny (which has excellent hardware support). Or of course you can just go back to Jaunty if that has worked for you. One note about the kernel link that I posted is that those are "mainline" kernels, which as I understand it may not have all of the specific device driver support that may be added by individual distro teams (so if you have a video card that requires something special, you might need to look for a Lucid kernel that's not "mainline").

Drag that Karmic is treating you so badly...

---

### Post by jcobban on 2009-12-05
> **fluffman86 said:**
>  Try pressing CTRL + ALT + F1 to get to a command line.  If you can log in there, run "sudo killall -9 Xorg" and then "sudo /etc/init.d/gdm restart"

The freeze prevents keyboard input, or at least prevents keyboard input from being directed to the appropriate process for handling.  Ctrl-Alt-F1 does nothing.

---

### Post by jcobban on 2009-12-05
> **blueridgedog said:**
>  Why not start a thread looking for a solution, rather than one implying that everything to do with your system is OK and the problem MUST be the kernel?

I am not a Linux guru, and have no expectation that I ever will be.  There are aspects of the behavior of the system that suggest several possible places.  Although my computer worked fine on Hardy, Intrepid, and Jaunty it only fails on Karmic.  I have now tried five different kernels running from 2.6.28-16 up to the latest Lucid RC with no improvement.  This does seem to rule out the kernel as the source, especially after I also tried 'nomodeset' with no improvement in reliability (although the performance problems on Intel graphics return if I do).

I **have **started threads over and over again asking for help.  I have **repeatedly** stated that my highest priority is to collect documentation that will permit resolving this problem.  **Nobody **has suggested any documentation that I could collect. I have attempted to follow every suggestion for resolving the problem except:
[LIST=1]
[*]Buy a new computer.  I am retired.  I do not have hundreds of spare dollars lieing around to spend on new computers.  In any event my wife would kill me if I bought a new computer while the existing one was at all functional.
[*]Install a different operating system which I would then have to spend days learning about, reconfiguring, reinstalling software on, and restoring all of my data to.  Even to go back to Jaunty would require restoring the system from backup and then restoring my current data files, which would be a couple of days of lost work.  And I wasn't that happy with Jaunty because of the performance problems with Intel graphics.  When it is actually working Karmic is significantly better.
[/LIST]

I do not feel that it is unreasonable that I should lose my temper when I am forced to suffer for weeks without getting any response to an apport report that the system is hanging.  I might be less upset if OOo did not throw all of my recent work in the trash when I reboot.

---

### Post by fluffman86 on 2009-12-05
Can you SSH into your frozen system?  See my post above...

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
Losing your temper is not as good as gaining patience. Would you rather lose or gain? Anyway... I had an issue with freezing when I first installed and come to find (after many days of frustration and head banging that did nothing for me) it was because my RAM wasn't seated properly. Considering it worked before I doubt that is the problem but it certainly does look like it may be a hardware issue. Try doing memtest and other diagnostics to ascertain if anything shows to be faulty. Not every problem can be explained nor sorted through the software.

---

### Post by blueridgedog on 2009-12-06
> **jcobban said:**
> Although my computer worked fine on Hardy, Intrepid, and Jaunty it only fails on Karmic.

I suggest you downgrade to Jaunty and decline the upgrade the breaks your system.

---

### Post by louieb on 2009-12-06
> **jcobban said:**
> [list]
[*]My system did not freeze on Hardy.  My system did not freeze on Intrepid.  My system did not freeze on Jaunty.  It **consistently** freezes on Karmic!
[*]I only have one system running Linux.
[/LIST]

Just wondering what is in Karmic that you absolutely have to have? 

When it comes to distribution updates, it is just good sense to make sure it works before trusting it for daily use. 

For me that means keeping my data separate from the OS. And having a partition set aside for testing. Lol thats why I'm still running Hardy on my desktop / web server / file server, Jaunty on my laptop, and my printer is connected to a PC running XP. 

By filing a bug report in lauchpad seems like you have done all you can.  I've filled out one or two myself.

---

### Post by michaelzap on 2009-12-06
> **louieb said:**
> Just wondering what is in Karmic that you absolutely have to have?

Well, obviously if Karmic just doesn't work and Jaunty does then Jaunty is the only viable option between the two. But I also had extremely annoying Intel video issues with Jaunty that made the Karmic upgrade more than just a desire for the latest thing. So I do feel for the OP in this situation, given that this is two releases in a row that have been problematic, to say the least.

That having been said, it doesn't seem as if the OP is entirely willing to spend the time and energy to solve this issue on their own. Frustration is understandable and a little venting can help to get it off your chest. But if you want Karmic to work on your system you're going to have to adopt a more patient attitude and troubleshoot you issues systematically, since only you can fix your system.

You didn't answer my question as to whether you'd tried the final Lucid kernel or the RC version (if there's an "RC" in the name, it's not the final version).

Check your system logs (System -> Administration -> Log File Viewer) and see if there's any helpful info in there as to what specifically is failing. I would look first in the kernel, xorg, and syslogs.

It sounds as if you are using a desktop system. Try disconnecting all but the essential hardware and see if it still crashes. A little more detail as to what hardware you have would also help people to help you.

---

### Post by jcobban on 2009-12-08
> **fluffman86 said:**
> 
Another thing to try...I believe you said your desktop was freezing, and you had vista on a laptop.  Now use the desktop as normal until it freezes.  When it does, look at your laptop to see if the clock is still ticking and see if any commands in particular are using a lot of memory.

If things are still running, then your kernel is still working.  If a particular command is eating a lot of CPU (like Xorg) then you can press 'q' to quit top, and then

sudo killall -9 Xorg
sudo /etc/init.d/gdm restart

and see if you get your system back that way.

I followed your advice and connected in the back way into the system.  top shows nothing at all unusual.  The usual server processes wake up periodically, but nobody is using more than a fraction of 1% of the CPU.

I tried issuing the two commands you suggested, but all that did was blank the display.  I still have to reboot the system to continue working.

---

### Post by jcobban on 2009-12-08
> **michaelzap said:**
> Well, obviously if Karmic just doesn't work and Jaunty does then Jaunty is the only viable option between the two. But I also had extremely annoying Intel video issues with Jaunty that made the Karmic upgrade more than just a desire for the latest thing. So I do feel for the OP in this situation, given that this is two releases in a row that have been problematic, to say the least.

That having been said, it doesn't seem as if the OP is entirely willing to spend the time and energy to solve this issue on their own. Frustration is understandable and a little venting can help to get it off your chest. But if you want Karmic to work on your system you're going to have to adopt a more patient attitude and troubleshoot you issues systematically, since only you can fix your system.

You didn't answer my question as to whether you'd tried the final Lucid kernel or the RC version (if there's an "RC" in the name, it's not the final version).

Check your system logs (System -> Administration -> Log File Viewer) and see if there's any helpful info in there as to what specifically is failing. I would look first in the kernel, xorg, and syslogs.

It sounds as if you are using a desktop system. Try disconnecting all but the essential hardware and see if it still crashes. A little more detail as to what hardware you have would also help people to help you.

I will admit that I am a pig-headed *** at times.  My major reason for not saying to h..l with Karmic and going back to Jaunty is that if this issue is not addressed I will never be able to move forward from Jaunty, and Jaunty is a pain to use on Intel graphics.  I want this problem resolved.  I do not want it hanging like the sword of Damocles over the entire community.

I tried 5 different kernels including the Lucid RC.  They all freeze.  I have gone back to using the most recently distributed Karmic kernel as it gives the longest MTBF of all of the kernels I have tried.

I am not a Linux guru.  I have only the vaguest notion of what diagnostic procedures to follow.  I have repeatedly asked for advice, and I have followed every piece of advice and collected every suggested piece of documentation that would not either cost me hundreds of dollars or several days of lost productivity.  I can look at the logs until the cows come home, but they are not going to tell **me **anything because I couldn't tell the difference between a normal log and an abnormal log.

For the most recent freeze I used putty to telnet into my desktop from my Windows laptop after the freeze.  I used top to look at what was running and could not see anything at all unusual.  The system was as idle as you would expect from the fact that X was not generating any events.  Every so often one of the server processes would burn a few cycles, before dropping back down again.  I then issued a reboot command from the telnet session, figuring that would be the least disruptive way to get the system running again.  When I look at the messages log after the reboot I see the following messages that might be relevant:
  
00:00:48 kernel: [129836.700150] [drm] DAC-5: set mode 1024x768 16
00:01:07 bonobo-activation-server (jcobban-12259): could not associate with desktop session: ...
00:04:43 kernel: kernel logging (proc) stopped

I assume that third message was a consequence of my issuing the reboot, and the kernel mode set seems to me to have occurred about the right amount of time before the reboot to be directly associated with the freeze.  The stream of messages associated with the new boot start at 00:06:05.

Although there are no time stamps to permit me to synchronize it with the messages log I note that in Xorg.1.log there is a message "Fatal server error: xf860OpenConsole: VT_WAITACTIVE failed: Interrupted system call"

Again I have no way of knowing what is significant and what is not in any of this.

---

### Post by michaelzap on 2009-12-08
> **jcobban said:**
> For the most recent freeze I used putty to telnet into my desktop from my Windows laptop after the freeze.  I used top to look at what was running and could not see anything at all unusual.  The system was as idle as you would expect from the fact that X was not generating any events.  Every so often one of the server processes would burn a few cycles, before dropping back down again.  I then issued a reboot command from the telnet session, figuring that would be the least disruptive way to get the system running again.  When I look at the messages log after the reboot I see the following messages that might be relevant:
  
00:00:48 kernel: [129836.700150] [drm] DAC-5: set mode 1024x768 16
00:01:07 bonobo-activation-server (jcobban-12259): could not associate with desktop session: ...
00:04:43 kernel: kernel logging (proc) stopped

I assume that third message was a consequence of my issuing the reboot, and the kernel mode set seems to me to have occurred about the right amount of time before the reboot to be directly associated with the freeze.  The stream of messages associated with the new boot start at 00:06:05.

Although there are no time stamps to permit me to synchronize it with the messages log I note that in Xorg.1.log there is a message "Fatal server error: xf860OpenConsole: VT_WAITACTIVE failed: Interrupted system call"

Again I have no way of knowing what is significant and what is not in any of this.

Sounds like an xorg/video driver issue and not a kernel panic to me. Are you using an Intel video chip/card? Try turning off Compiz effects (System->Preferences->Appearance->Visual Effects->None) and seeing if it crashes after that.

This thread looks related: [http://ubuntuforums.org/showthread.php?t=1317918](http://ubuntuforums.org/showthread.php?t=1317918)

---

### Post by MaxIBoy on 2009-12-09
Try using Xvesa instead of Xorg. At the GRUB screen, hit "e" to temporarily edit the boot parameters for the kernel you normally use. Add "xforcevesa" to the kernel's parameters. Then go ahead and boot.


Your screen resolution will be limited, performance is going to be terrible, and you can just forget about any 3D stuff. Probably not a long-term solution. But it would help to narrow down the problem, and I predict that it will not crash.

---

### Post by jcobban on 2009-12-09
> **michaelzap said:**
> Sounds like an xorg/video driver issue and not a kernel panic to me. Are you using an Intel video chip/card? Try turning off Compiz effects (System->Preferences->Appearance->Visual Effects->None) and seeing if it crashes after that.

This thread looks related: [http://ubuntuforums.org/showthread.php?t=1317918](http://ubuntuforums.org/showthread.php?t=1317918)

Thank you.  

I am already running with Visual Effects set to None.

I am confident that the problem **is** related to the Intel graphics chips.  However since most computers in the world have Intel graphics chips I would have thought that support for those chips would be a priority.

I am not seeing the messages that are reported in that other problem.  I just experienced the freeze again.  After the reboot, which I now perform by telnetting into the otherwise perfectly running system and issuing a reboot at the command line, I looked in the messages log.  There are **no** messages for almost 2 hours prior to a message about shutting down the log, which presumably is a result of my issuing the reboot.

The primary reason I am leaving my system in this painful state is so I can collect documentation that will lead to a resolution of this problem.  However if nobody is going to bother looking at the problem reports then the problem will never be resolved.

All I want for Christmas is for somebody to **look** at this problem!

---

### Post by gpstar on 2009-12-09
Just a question, but what processes/programs do you have running?

I was having similar issues with karmic freezing on my laptop. My system logs would not show any hints at what was freezing. It would always be a random complete lockup, mouse wouldn't move, screen frozen, keyboard unresponsive. I could tell when it froze because the time on the desktop showed when it happened. I tried various new kernels, etc etc, and nothing would solve it.

Eventually I started closing programs one by one and letting the computer idle until it would no longer do the random freezing. Eventually i traced it back to the Screenlets I was running.



> **jcobban said:**
> Thank you.  

I am already running with Visual Effects set to None.

I am confident that the problem **is** related to the Intel graphics chips.  However since most computers in the world have Intel graphics chips I would have thought that support for those chips would be a priority.

I am not seeing the messages that are reported in that other problem.  I just experienced the freeze again.  After the reboot, which I now perform by telnetting into the otherwise perfectly running system and issuing a reboot at the command line, I looked in the messages log.  There are **no** messages for almost 2 hours prior to a message about shutting down the log, which presumably is a result of my issuing the reboot.

The primary reason I am leaving my system in this painful state is so I can collect documentation that will lead to a resolution of this problem.  However if nobody is going to bother looking at the problem reports then the problem will never be resolved.

All I want for Christmas is for somebody to **look** at this problem!

---

### Post by bshosey on 2009-12-09
jcobban: Could it be the new Intel Video drivers. I had problem with resolution and stuttering courser. I even had the system lock up once on me. I have an Intel 845. I downgrade the video driver to the 9.04 drivers and have not had a hick up sense. This system never gets shut off. 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

is the link I got the information to do so. I hope this helps.

---

### Post by jcobban on 2009-12-10
> **bshosey said:**
> jcobban: Could it be the new Intel Video drivers. I had problem with resolution and stuttering courser. I even had the system lock up once on me. I have an Intel 845. I downgrade the video driver to the 9.04 drivers and have not had a hick up sense. This system never gets shut off. 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

is the link I got the information to do so. I hope this helps.

This item describes performance problems with Intel chips.  I observed those problems, and they were annoying.  However the fix which the development community chose to deploy for those performance problems is Kernel Mode Set (KMS), which is implemented in Karmic and works.  The fact that KMS resolves the performance problems is one of the reasons, although not the most important, for my reluctance to go back.  In any event when I disable KMS in grub I revert to the bad graphics performance but still encounter the freeze!

I would strongly prefer to move forward, rather than backward.  Jaunty was an annoying system to use on my computer, so I moved to Karmic prematurely.

---

### Post by bshosey on 2009-12-10
I understand that you do not want to move backward. I was not saying this is a permanet change. I just wanted you to try it and see if you still have the lockups. This was an easy and fast test to see if it is a driver issue or a kernel.

---

