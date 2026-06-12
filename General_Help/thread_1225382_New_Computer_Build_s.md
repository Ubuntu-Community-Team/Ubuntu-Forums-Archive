---
title: "New Computer Build ?s"
date: 2009-07-28
forum: General Help
---

### Post by anotherdisciple on 2009-07-28
I am building a computer in a few months with these specs:

[LIST]
[*]Intel Core i7 920 2.66GHz
[*]6GB of DDR3 1600
[*]nVidia GTS 250, 1GB GDDR3
[*](3) 640GB Western Digital Caviar Black 7200 RPM Hard Drives
[/LIST]

If you need to know anything more... let me know.

So, I have a lot of questions.

1) Should I bother with 64bit Ubuntu? 
[INDENT]I will have a wireless N card that I think I would run into trouble with... and I love testing out new FOSS, so I would likey be unable to run much of it. However, that 6GB of RAM will be a waste without 64bit!!![/INDENT]

2) I am setting up (1) HD for Linux, (1) _MIGHT_ be for Windows 7 if it's any good, and (1) will be for all my files. So, what is the best way to share files between Windows and Linux? I want to use EXT3 or EXT4, but I don't know how Windows will handle that.

3) Would it be better to use Windows in VirtualBox? 
[INDENT]I'm thinking I would lose some advantages. I have an iPod Touch 2nd Generation... and the best way I can find to sync it is with Windows, but I doubt a virtualized OS will let me sync it.[/INDENT]

4) Do you see any potential problems with my hardware choices in Linux?

ummm.... I think that's all I have for now...

---

### Post by DeMus on 2009-07-28
> **anotherdisciple said:**
> I am building a computer in a few months with these specs:

[LIST]
[*]Intel Core i7 920 2.66GHz
[*]6GB of DDR3 1600
[*]nVidia GTS 250, 1GB GDDR3
[*](3) 640GB Western Digital Caviar Black 7200 RPM Hard Drives
[/LIST]

If you need to know anything more... let me know.

So, I have a lot of questions.

1) Should I bother with 64bit Ubuntu? 
[INDENT]I will have a wireless N card that I think I would run into trouble with... and I love testing out new FOSS, so I would likey be unable to run much of it. However, that 6GB of RAM will be a waste without 64bit!!![/INDENT]

2) I am setting up (1) HD for Linux, (1) _MIGHT_ be for Windows 7 if it's any good, and (1) will be for all my files. So, what is the best way to share files between Windows and Linux? I want to use EXT3 or EXT4, but I don't know how Windows will handle that.

3) Would it be better to use Windows in VirtualBox? 
[INDENT]I'm thinking I would lose some advantages. I have an iPod Touch 2nd Generation... and the best way I can find to sync it is with Windows, but I doubt a virtualized OS will let me sync it.[/INDENT]

4) Do you see any potential problems with my hardware choices in Linux?

ummm.... I think that's all I have for now...

1:
Wireless: hate it. Have a cable all the way through the house and have an optimal connection to my router this way. Know nothing about wireless, never use it.

2:
6GB ram: you definitely need 64bits OS
640GB disk: it's a waste to use one whole disk just for the OS, a second one for another OS and only the third for data. Ubuntu runs on 15-20GB so why use 640GB?
Think about placing the disks in raid:
raid 0 for more speed and full disk size
raid 1 for complete safety but half the disk size
raid 5 for safety but 2/3 of the disk size

3:
Don't use a virtual box. One OS depends on the other. Use it side by side in a dual boot.

4:
No

---

