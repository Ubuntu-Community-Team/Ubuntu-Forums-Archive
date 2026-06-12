---
title: "How to remove Ubuntu and fix the MBR for Vista"
date: 2009-11-07
forum: General Help
---

### Post by MerlinsLair on 2009-11-07
First off, I've read many of the threads concerning this particular situation but have run into a problem with the Recovery DVD. Upon selecting the language, time, currency, keyboard, etc. and then selecting next...there is no option for Repair Computer. Not even if I deselect my Vista OS (which by the way, is the only one listed).

So this begs the question: What next?

I need to remove Ubuntu from the machine as I'm giving it to my daughter for her use in school. Reinstalling Vista is not an option here either as there is a lot of software and data that she'll need already installed.

I read a thread about an .exe file called mbrfix.exe? Will this do what I need and if so, is there anything in particular I need to know in advance before proceeding?

Just for a FYI, I have not removed any partitions yet, it is a dual boot with Vista and Ubuntu 9.04 on a 64 bit system.

Thanks for your time and help.

---

### Post by mbuell on 2009-11-07
I think you'll find enough in these links to fix your situation. Just one thot - why not just let your daughter continue to use grub to start Windows? Grub works to start windows even if the Linux distro is uninstalled. Just a thot.

[URL="http://www.webtree.ca/windowsxp/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:"]http://www.webtree.ca/windowsxp
/repair_xp.htm#How%20to%20Repair%20the%20Boot%20Sector:[/URL]
[http://askbobrankin.com/fix_mbr.html]("http://askbobrankin.com/fix_mbr.html")
[http://support.microsoft.com/kb/314058]("http://support.microsoft.com/kb/314058")
[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm")

---

### Post by MerlinsLair on 2009-11-07
Thanks for the links. I'll go over them and see what will work out for my situation. As for my daughter, sigh, what can I say? She's right. I'm wrong. Ugh! Teenagers! Thanks again for the help mbuell.

---

### Post by vttay03 on 2009-11-07
Ran into this same issue awhile back when I was booting Ubuntu off an external drive and when I installed it, it overwrote the windows bootloader.  Therefore, if I didn't have the external drive plugged in when I booted the computer, I could never boot Vista.  Anyways, I used a free application named EasyBCD to restore the Windows bootloader.  Worked like a charm....don't know if this could help you or not.  I don't remember a whole lot of the details but you may want to check it out....

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by nathanernest on 2009-11-08
fixmbr is a exe that you can run from the recovery console using the windows vista disc. Dont worry about removing ubuntu, you can simply format the partition when you get back into windows. So to do this is easy,

1. Boot from the Vista Disc and select "repair your computer" in the bottom left corner of the window.
2. When the options come up there should be a choice of recovery console.
3. Simply type "fixmbr" and then "y" to confirm. This will rewrite the master boot record (where grub probably installed) and simply  boot straight into windows.
4. Open disc managment in vista and delete the ubuntu partition. Then resize the partition to expand into the empty space that ubuntu once lived.

Good stuff, that windows recovery tool!

---

### Post by MerlinsLair on 2009-11-08
Sorry for the late reply but the recovery disc that came with the Lenovo has no such Repair Computer choice. Just to reinstall the OS which isn't what I need to do obviously. Am looking over the other info atm. Will let you know how this works out when I finish. ;)

---

### Post by MerlinsLair on 2009-11-08
vttay03, you're the best! Actually, I appreciate all the help and the useful links. I was able to reinstall the Vista bootloader in seconds after downloading and using the EasyBCD program. Glad it's free but after this experience, I went back and contributed to their work.

This little app has a lot of useful features in it as well and may be a good idea for anyone out there to try out if they're looking to give a dual-boot a try.

Again, thanks for the help. This is why I like this community. Everyone always has time to help or offer advice. :D

---

