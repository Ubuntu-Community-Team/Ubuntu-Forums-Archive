---
title: "Ubuntu not booting after standby hard reset"
date: 2009-09-23
forum: General Help
---

### Post by Joe of loath on 2009-09-23
Hi there

Last night I set my dell inspiron 1545 laptop on standby. I started it this morning, and it froze on the unlock screen. I tried ctrl-alt-F1 all the way to F7, and none of them worked. So I held the power button, and rebooted. However, it seems something is up. It's dropping me into busybox, with a few error messages above the prompt about failed mounts. I hope my disk isn't corrupted... Sorry I can't elaborate, not much to say. Has anyone experienced this issue before? Is there any way to save my install, other than using a live CD to backup my /home file?

---

### Post by MelDJ on 2009-09-23
did you install ubuntu with windows? then do a chkdsk. busybox comes when the computer is not shut down properly. its like a last resort for ubuntu. if you dont have windows, drop to a shell and run fdisk

---

### Post by Joe of loath on 2009-09-23
No, it's installed on a seperate partition. I'll try fdisk, and see what happens!

---

### Post by Joe of loath on 2009-09-23
I think you meant fsck? Fdisk doesn't do what I need. I'm running an fsck, but not sure how well it'll work. I can't even mount the disk, so no way to recover my data! No more standby for me I think...

---

### Post by MelDJ on 2009-09-23
do you mean that you installed ubuntu and windows on the same disk? then run chkdsk on the drive

---

### Post by Joe of loath on 2009-09-23
:confused: I don't think I ever mentioned windows or wubi... Anyway, I think fsck worked, I can mount the drive now, so at least I can pull my data off.

---

### Post by MelDJ on 2009-09-24
sorry about that. i thought you meant you installed windows with ubuntu:)

---

### Post by HieronymusBosch on 2009-12-17
I also have this problem.  If I hard reset my computer (it sometimes fails to come back from standby), ubuntu becomes corrupted and hangs at the loading screen.  There isn't anything on the boot drive except for the operating system, so I've just had to reinstall whenever it happens.  It happened with 9.04 and now 9.10.  I don't have any other operating systems installed and luckily all of my data is kept on a separate drive.  I'm not sure if this is a hardware issue or if it is a problem related to ubuntu.

---

### Post by hansdown on 2009-12-17
There is a much safer way to reset your computer. It does take a little practice.

[http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html)

The ubuntu reference sheet from fosswire has some good tips.

[http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

---

### Post by jbslaw on 2009-12-18
You need to determine why your system locked up  Many hangs after suspending are caused by video problems.  If you set your visual effect to "none" ("System/Preferences/Appearance/ click on the "visual effects" tab) your system will have less to do and will therefore be more stable, though less sexy.

---

### Post by HieronymusBosch on 2009-12-27
I have my visual settings set to 'none,' already (otherwise, I have trouble using the desktop remotely from my laptop).  I don't have the system set to hibernate, and this time around I am not going to let it even turn the display off to see if that changes anything.  I will definitely use alt+printscreen+R+E+I+S+U+B next time (thank you!), and report back if it doesn't help.

---

