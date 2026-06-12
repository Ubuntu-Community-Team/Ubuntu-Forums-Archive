---
title: "Used mkfs.ext3 on wrong partition, Help please"
date: 2012-04-08
forum: General Help
---

### Post by Budisha on 2012-04-08
Like the title says, i accidentally formatted the wrong partition. My main, windows partition.
I thought i was formatting my USB drive. When i formated it. I rebooted into grub and tried to select windows, but got an error which i dont remember. I think it was "Error: couldt not find partition."
After i almost hyperventilated from the shock, I tried using the windows recovery CD. I started the command prompt and used the following command:
```

bootsect /nt60 SYS /mbr

```I rebooted and when grub should have booted, i got an error. It wasnt a grub error, grub didnt even start. Again, i dont really remember what the error said. I think it was "Could not find boot" or "Could not find partition". After that i started the windows reccovery cd and command prompt and used theese commands:
```

bootrec /FixBoot

```and
```

bootrec /FixMbr

```I rebooted again and again i got an error before grub, but it was a different error. It said "A disk read error occurred. Press ctrl + alt + del to reboot".

I'm at the end of my nerves. Is there a way i can recover this? Please help me, im desperate. :cry: Thanks

Sorry about the spelling errors. I'm on my laptop with the annoying keyboard.

---

### Post by rmil on 2012-04-08
Unfortunately you did several writes to MBR. Try with testdisk it might find deleted ntfs partitions. Honestly the chances are not so good. 
Secondly depends on Windows version but generally you boot windows rescue CD and then try fixmbr.


Suggestion for everyone reading this: When you make such mistake first you make pause of 15mins drink coffee or something else to cool down. Then you do backup of destroyed partition with command dd and after finishing you play with MBR writing.

---

### Post by rmil on 2012-04-08
Addition to second option: 
Second option might make ubuntu not booting.

---

### Post by alzyee on 2012-04-08
If you have the spare disk space do like rmil said and use dd to make a copy of that partition before you do anything else. 

This might be useful
 [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by Budisha on 2012-04-09
God, this is getting worse and worse. Today i turn on the pc trying to boot off the Ubuntu live cd, but it frooze in the middle of the bios screen. It scans through the IDE channels (i dont even know what this means) and then comes a black screen and just freezes. Any ideas? Maybe i could do something with the drive if i put it in another computer? 
Thanks for your help. I really appriciate it.

Edit.
I managet to boot from the ubuntu 11.10 live cd. I guess it was just something with the screen. :\

Edit. Tried testdisk and fixmbr. Nothing changed. :cry: I cant use dd because i dont have a spare disk to copy to. Any more suggestions?

---

