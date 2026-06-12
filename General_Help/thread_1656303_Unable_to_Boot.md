---
title: "Unable to Boot"
date: 2010-12-30
forum: General Help
---

### Post by Nexus35 on 2010-12-30
Problem:
Error: no such device: f50139a2-b475-4ef5-8217-051bd145a24e.
grub rescue> _

I know it is saying that the harddrive that I installed ubuntu is missing.

Heres the story:

My friend's computer wouldnt let him boot to the CD to install Ubuntu on his computer.

So I put his harddrive into my computer as my 3'rd Harddrive and booted the CD on my Machiene and installed Ubuntu to his harddrive.

We got ubuntu to work just fine, and then I removed his harddrive from my computer... big mistake. I no longer have the harddrive that we installed ubuntu to so I cannot use any programs or anything.

What I want to do is get my Windows 7 working again. Right now I cannot do ANYTHING.

I have tried:

Windows Boot Recovery (failed)
System Restore (failed)
changing many bios settings (failed)
Flashing the bios (failed)

Any help would be much appreciated.

---

### Post by oldfred on 2010-12-30
Welcome to the forums.

I would have thought that the windows boot recovery would have worked. Did you run fixMBR or BootRec.exe /fixmbr  depending on version of windows. When you installed Ubuntu it often defaults to the boot drive, usually sda. You wanted to use manual install so you could choose to install grub to sdd or whatever drive your friends was. He probably is missing grub on that drive's MBR also.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From a liveCD run this and we can see what is where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Nexus35 on 2010-12-30
Thank you very much!!

"http://ubuntuforums.org/showthread.php?t=1014708"

and "bootsect /nt60 C: /mbr" solved the problem.

Eachtime when I tried using the recovery tools I always had "Windows 7" selected, which I think wasn preventing the commands from fixing this.

[SOLVED]

---

