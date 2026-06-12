---
title: "video not playing , firefox lag"
date: 2009-06-29
forum: General Help
---

### Post by pantera10 on 2009-06-29
hi im kinda new to ubuntu.. im running a HP laptop , intel 965 ..on a monitor

heres my problem .

when i installed ubuntu i realised tht the intel gfx drivers are not installed..and so i followed a few instructions and did that...upon doing tht...the resolution i was getting on the monitor got screwed..i was not getting the whole part of the desktop and auto-image adjust was not working..so i searched it on google..and found a couple of fixes.

one of them was installing something frm synaptic..and i did tht...
the other one was something to do with xorg.conf and it asked me to copy paste the whole command and restart X...

i accidently did both fixed and restarted X...and then the laptop started to make this beep sound till i shut it off manualy...and now whenever i try to run a video i get this werid black purple screen and after a second or two im back to the login screen..PLUs , firefox is lagging like a B****.

...i would prefer to go back to the way thigns were when i installed ubuntu :P ..or ofcourse a FIX would be useful too..since im not  since im not tht keen on resintalling ubuntu !..also if anyone can post a default xorg.conf for intel 965 ..i could copy paste tht onto mine and tht might fix it..but thts just my thought..im kinda clueless

---

### Post by Laysan_A on 2009-06-29
Hi pantera10,

X should reconfigure to its default (safe) mode automatically if you reboot, and at the screen where it shows your kernels, choose recovery or recover (whatever it is, you'll see). Then just arrow down (it's past what's shown, I think) to "recover graphics" or something similar (actually, I think it might be "reconfigure x"). Hit enter and follow the instructions. After a reboot you should have a usable screen. 

If your new graphics driver caused this problem (it wasn't entirely clear to me from your post) you should uninstall it. If you can get into synaptics package manager, find it and remove it.

If something has happened and x won't/can't reconfigure automatically and you cannot get into your desktop, you'll have to work from the command line. If you know the exact name of the driver package you installed you can type
sudo apt-get remove [I]drivername
[/I]and that will get it out of the way. That may be enough for the recovery option at boot-up to work. 

If you don't know the exact name of your driver (and no one here supplies it for you) you can find it (it may take you a while, though) by typing *aptitude* at  the command prompt. Select i*nstalled  packages* by arrowing down and hitting enter, and then proceed to go through the entries of all your installed packages, starting with the most likely category first (open each level of the tree by first selecting then hitting enter). Once you know the name, you can sudo apt-get remove it.

After you've uninstalled your offending driver, open a terminal and type
[I]sudo apt-get -f
[/I]and that should (hopefully) repair any damage left behind.

---

### Post by lovinglinux on 2009-06-29
To reset xorg settings: [http://ubuntuforums.org/showpost.php?p=5717943&postcount=2](http://ubuntuforums.org/showpost.php?p=5717943&postcount=2)
To improve your graphics card performance: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
To improve Firefox performance: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by nonzer0 on 2009-06-29
Try to restart your computer, boot into recovery mode, choose to repair x-server, and repair broken packages.  I had a similar problem with my brothers PC and it worked.

---

### Post by pantera10 on 2009-06-30
im going to try the aptitude thing tht layson has mentions and report back with results...

nonzer0 : how do i boot into recovery mode :S 

btw...ive just realised tht everything i do is lagging..even when im viewing picturs or opening a folder , etc etc

---

### Post by lovinglinux on 2009-06-30
> **pantera10 said:**
> btw...ive just realised tht everything i do is lagging..even when im viewing picturs or opening a folder , etc etc

Follow the links on my previous post.

---

### Post by Laysan_A on 2009-07-01
@Pantera10

I'm sorry to hear ubuntu is running slow for you. I've run across a few folks who have been experiencing the same thing. I wish I could help. Have you tried searching for your symptoms specifically, for instance, how's your processor load? If it's high for no apparent reason, try searching for that, too.

I had what sounds like a similar problem after I switched to a 2.6.29 kernel. I never knew what caused it. It went away when I compiled a .30 kernel. 

Maybe the Intel "How To" will fix it.

(I explained how to boot into recovery mode in the first paragraph of my previous post)

---

### Post by pantera10 on 2009-07-01
ok i have fixed it...tahnk u all for ur support...nonzer0s fix was spot on and it helped me get back to the stage i was at before...which is much better then the super lag i was facing...though my monitor screens were adjusted perfectly :( 

oh well..i guess i'll have to wait for intel to get out of the blacklist

---

