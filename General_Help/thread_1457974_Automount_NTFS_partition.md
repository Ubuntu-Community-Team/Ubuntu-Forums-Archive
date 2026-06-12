---
title: "Automount NTFS partition?"
date: 2010-04-19
forum: General Help
---

### Post by h4x0rmx on 2010-04-19
I have a 500GB HD in which I have 3 NTFS partitions and 3 other partitions for Linux. 2 of the NTFS partitions are mainly used for storage and I created them when Windows was my primary OS. Now that I'm moving to Linux I want to be able to access those partitions as if they were native partitions on Linux, but I'd like to auto mount one or two of them. I do want to keep them as NTFS since I still want to be able to use them on windows (I have some windows projects, so I can't get rid of it) since -I believe- Windows doesn't support ext2/3 partitions. Is that possible? Is there any risk of doing that?
I'll appreciate your help.

P.S. Please be as explicit as possible on your answer :)

---

### Post by sunnyengineeer on 2010-04-19
Hello,
          Gud to hear that u r kicking Windows.....
For AutoMounting of NTFS drives which u had in Windows,,,Ubuntu has a software
to do that,only once u've to mount the drives which u want to be mounted
It is NTFS Configuration Tool...It will solve ur said proble..I also had this...
While u mount drives,remeber to check Write access in the radio button of the tool...

Thanks
Every Windows has glasses,so it will always crash...

---

### Post by h4x0rmx on 2010-04-19
@sunnyengineeer: I can mount the NTFS partitions without a problem, I'm just wondering if I can _auto_-mount them? :)

---

### Post by coffeecat on 2010-04-19
This is entirely feasible. NTFS read-write is reliable in Ubuntu and I use shared NTFS data partitions in two of my machines. I also have a number of NTFS-formatted external drives which work quite happily with Ubuntu. One caveat with using NTFS is that you must have Windows available in the unlikely event that the NTFS filesystem becomes corrupted, in which case you'll need to run chkdsk from Windows.

I assume you mean the 500GB hard drive is an internal one, because NTFS-formatted external drives will be automounted as soon as you plug them in.

For an internal drive you can get down and dirty, create mountpoints and edit [/etc/fstab]("https://help.ubuntu.com/community/Fstab"). But a simpler way would be to install the package ntfs-config which gives you a GUI utility to do what you want.

---

### Post by h4x0rmx on 2010-04-19
If you put it that way, I guess the NTFS partitions are auto-mounted, but I have to enter a password every time I want to access them.  I have some programs (like Vuze) that try to access those partitions as soon as I open them. Of course, if I haven't entered my password they won't have access to them. Is there a way to skip this password thing?
I know it's done for security reasons and stuff, but it'd be nice to bypass it since I know what I'm doing

---

### Post by coffeecat on 2010-04-19
> **h4x0rmx said:**
> If you put it that way, I guess the NTFS partitions are auto-mounted, but I have to enter a password every time I want to access them.  I have some programs (like Vuze) that try to access those partitions as soon as I open them. Of course, if I haven't entered my password they won't have access to them. Is there a way to skip this password thing?
I know it's done for security reasons and stuff, but it'd be nice to bypass it since I know what I'm doing

Let's clarify something: if you mount an **internal** NTFS partition from the Places menu, you are prompted for your password. If you plug in an **external** NTFS drive, it gets automounted without you having to enter your password.

But if you arrange for your **internal** partitions to be automounted on bootup as I describe in my previous post (edit /etc/fstab or use ntfs-config) then you don't have to enter your password.

---

### Post by h4x0rmx on 2010-04-19
Sorry! I must have skipped that part! 
I'm going a give it a try when I get home and then I'll report.

---

### Post by h4x0rmx on 2010-04-20
nice! That was easy! It works perfectly!
Thanks guys!

---

