---
title: "Solve WinXP3 problem with Ubuntu 9.04?"
date: 2010-12-26
forum: General Help
---

### Post by oldbilbobaggins on 2010-12-26
Hello from a 'noob lurker' and not a very sharp one at that.

Can anyone guide me towards fixing the Win problem below using Ubuntu 'jaunty'?

....On a DellDim E520 running XP3 ( on C:\ partition ) I downloaded/installed a 'sandbox' type app called BufferZone Pro ( on D:\ partition ). The installation called for a reboot, which I OK'd. The restart ran through the Win splashscreen/jingle to 'Loading your personal preferences' and should then have displayed my standard desktop with app icons/shortcuts.

Instead I got a lightblue background and NO app icons/shortcuts. Nuttin' apart from a moveable but non-functioning cursor.

The BZP app seems to have locked me out of everything, while keeping Windows up and running.

'Safe Mode' gives an apparently-OK Win startup, then a black screen with 'Safe Mode' in the corners, a moveable cursor, and no options.

'Last known working  config' produces, after the Windows splash screen, the same blank  lightblue background screen - with no icons and no options. It seems  the system thinks that Windows starts up OK, and that BZP is doing what  it should, so the last known working config is exactly that.... 

I can get into a 'Safe Mode with command prompt' mode, and can input DOS  instructions, but I need advice on whether and how this can be used to  uninstall BZP or initiate a Restore Point far enough back. I have the Dell Restore disc, but I believe that wipes all data, which I'm unwilling to accept. There must be a way into this system which permits me to 'reel back' the functioning of BZP, short of a reformat and data loss.

I've boot/started the machine using a Ubuntu 9.04 'live disc' which lets me see  the directory which holds the BZP folders, but I don't know how to use  that Ubuntu OS to uninstall the errant program. 

Maybe, if there's a way, you guys can tell me how.

Anyone know? I'm happy to receive emails on this...

:icon_frown: oldbilbobaggins

---

### Post by wilee-nilee on 2010-12-26
You download this from a torrent or buy it?

Do you have a actual Ubuntu install on the computer?

So your expecting us to know how to fix a 3rd party MS software on the Ubuntu forums?

---

### Post by oldbilbobaggins on 2010-12-27
I regret that you seem rather offended, Mr WilliNilli, for I'm sure you are a helpful, pleasant guy face-to-face.

The distro was provided to me by Canonical Ltd. I quote from the sleeve....

> **The Ubuntu community**

The Ubuntu community is what makes Linux special. We'd love you to join us! Visit *[www.ubuntu.com/community]("http://www.ubuntu.com/community")* to learn howI have no expectations whatsoever.  Now, 'hopes and aspirations', that's different. I am well aware that many peeps on many forums know much more about lots of stuff than I myself. For my part, I do try to pass on the little knowhow that comes my way, whenever it seems both helpful and appropriate.

Someone, somewhere will pop up and tell me "No, you can't - and here's why!" or "Yes, you can - and here's where to look for how!"

Many thanks for your response.

Oldbilbo

---

### Post by WorMzy on 2010-12-27
Unfortunately, Ubuntu isn't a Windows repair tool, it's an operating system. If you can solve your problem by deleting/moving/editing files on the Windows partition, then you can do this from Ubuntu, but if you're hoping there's a "Fix Windows" application that will find out what the problem is and then fix it, you're going to be very disappointed.

You should try asking on a Windows forum.

---

### Post by tredegar on 2010-12-27
Windows (which I know little about) appears to be broken.

But you can boot to ubuntu, and use ubuntu to save your personal data that is on the windows disks to somewhere else ( a USB drive? ) and then maybe try re-installing windows from your restore disk.

Good luck.

---

### Post by fluffman86 on 2010-12-27
> **tredegar said:**
> Windows (which I know little about) appears to be broken.

But you can boot to ubuntu, and use ubuntu to save your personal data that is on the windows disks to somewhere else ( a USB drive? ) and then maybe try re-installing windows from your restore disk.

Good luck.

This. Looks like BufferZonePro has messed around with your partitioning and boot options. Here's something you can try:

1. Boot Ubuntu and use it to backup all of your important files. Worst case is what I tell you will wipe your drives, but that's the last resort anyway, so it won't hurt to go ahead and BACK UP.

2. After backing up, head into System > Administration > Gparted (or Partition Manager, depending on the version of Ubuntu) and take a screen shot of what you see there and post it here. To take a screen shot, just press PrtScr on your keyboard and it should ask you to save the picture.

*PAUSE HERE*

3. Once we verify what's what, delete the partition containing BZP and grow your other partition to take the rest of the space.

4. Boot into your Dell recovery disc, and from there go to the recovery console. It will ask you to enter the Admin password, which is blank (just press enter), unless you set one yourself. Then when you get to the command prompt, type "fixmbr" and press enter, then follow the prompts and type "exit" to reboot. Take out the CD when the computer starts to boot again.

5. Try booting into Windows now. If it boots properly, it will want to run a check disk (chkdsk) on boot. Let that run and see if Windows boots properly.

6. If windows doesn't boot properly, boot from the recovery CD again. This time try running a repair install. This *should* only over-write critical Windows files and maybe some programs, but leave your files alone. If your disc is for SP2 instead of SP3, you'll need to run your updates again.

7. If none of that works, boot into Ubuntu again and install it. :D Or, you can boot into the Dell CD again, delete your partitions altogether, create a new partition from the free space (select "Quick Format"), and install Windows again on that space. THIS STEP WILL ERASE DATA PERMANENTLY! But that's why we ran a backup earlier. :)

---

### Post by Rubi1200 on 2010-12-27
I agree with tredegar that you need to try and salvage at least some of your data.

I have had good experiences with Knoppix for this purpose in the past.

I also think that *if* this software caused these problems that you should address some of your queries towards the company that produces and sells it.

In many cases, unfortunately, reinstalling is often the only way to deal with these types of situations since tracking down the exact cause and location of the problem can be very difficult.

Another option is to use Testdisk to try and recover data:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by dandnsmith on 2010-12-27
What I'd try at this point is getting safe mode started, with as little running as possible, and then get into msconfig - you can do this from the command line - and disable any startup calls to the bzp stuff (you need to look carefully at it).

This may be sufficient to get you going again (at which point I'd recommend uninstalling the stuff)

HTH

---

### Post by oldbilbobaggins on 2010-12-27
Many thanks, guys!

This 'bear of little brain' now has several pointers to prioritise and work at over the next few days....

Appreciated.

:KS

---

