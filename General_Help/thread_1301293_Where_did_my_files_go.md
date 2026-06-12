---
title: "Where did my files go?"
date: 2009-10-25
forum: General Help
---

### Post by CupofDice on 2009-10-25
I have a seagate external harddrive formatted in ntfs. I tried to move all of my folders/files off of it and onto my comp, but some are turning up missing. When I use Dolphin, it tells me 'could not read /media/disk/folder', but what is worst is that the files disappear and the folder ends up in my /home/user with no files inside them.

So, does anyone know where my files went? Also, is there a program that can look at my HD and show me what is taking up space?

Edit: I didn't have ntfs installed. I assumed that 9.04 was able to read from ntfs automatically, but I am installing it now.

---

### Post by CupofDice on 2009-10-25
Bump. Anyone have any ideas? I checked all of my trash folders and possible suspects with a root Dolphin, but I found nothing.

---

### Post by Old *ix Geek on 2009-10-26
> **CupofDice said:**
> I have a seagate external harddrive formatted in ntfs. I tried to move all of my folders/files off of it and onto my comp, but some are turning up missing. When I use Dolphin, it tells me 'could not read /media/disk/folder', but what is worst is that the files disappear and the folder ends up in my /home/user with no files inside them.Just to clarify: Are you saying that the files no longer exist on the external drive AND they're not on the internal drive? Also, by what method did you attempt to move them, i.e., via command line commands or drag/drop?
> Also, is there a program that can look at my HD and show me what is taking up space?Take a look at **/usr/bin/baobab**. It provides a graphical look at your file system(s).

---

### Post by CupofDice on 2009-10-26
Thanks for responding!

The first time, I moved by the terminal since Dolphin (wasn't using the latest kde 4 then) kept crashing. The files did not disappear from my ext HD, I believe.

The second time (yesterday), I moved by Dolphin and the files and folders disappeared from my ext HD, but only a folder showed up on my internal HD, with nothing inside it.

Edit: I installed XP in virtualbox, and after a lot of b****ing with Vbox and user groups and usbs, I am now taking my files from my ext hd onto my XP and will move them to my internal hd that way.

---

### Post by barlaso on 2009-10-30
Hello, I have the same problem.  I backed up my home folder to an ntfs usb hdd.  I upgraded to karmic, and some folders that i backed up now look empty.  When i run ls -la on them, it shows 20 total items, but those files / folders have disappeared.  

Could you please post a step by step solution, if you were able to recover your files?

---

