---
title: "How to run testdisk"
date: 2011-11-21
forum: General Help
---

### Post by badboy1 on 2011-11-21
> **Bigtime_Scrub said:**
> Try opening up a terminal and type "testdisk" in it and hit enter. See if that runs the program. I am not sure but I think it has no GUI and is a terminal only program.

hi i am really, honestly TOTALLY new at linux, and im trying to get some data back using test disk and i installed it using the ubuntu software center and i tried running it via terminal and i get this, can you tell me what should i do next please i would appreciate your help..thanx

to run a command as administrator use "sudo <command>".  see "man sudo_root" for details

---

### Post by alphaamanitin on 2011-11-21
It is trying to tell you that you need to run the testdisk command as root.  So, ```
sudo testdisk
``` is what you want to run.  

I think you should read the testdisk manual for the remaining steps.  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)  Seriously, it is an amazing program with great instructions.  You should be on its website.  I have used to to recover a 250 NTFS drive that I quick formatted to FAT32.  I not only recovered the data, but the operating system as well, all done by following the TestDisk creator's instructions.  Also, you should probably make your own thread. And bad news, depending on how long you have been using the device you have been trying to recover the data from, it could be complete gone by now.

AlphaA

---

### Post by coffeecat on 2011-11-21
@badboy1, you necromanced a 3+ year old thread. It's better to start your own one, so I've split your post and alphaamanitin's reply off into its own thread.

Testdisk should only be used in certain circumstances. You might want to post details of why you are trying to use it so that forum members can advise you best.

---

### Post by alphaamanitin on 2011-11-22
> **coffeecat said:**
> @badboy1, you necromanced a 3+ year old thread. It's better to start your own one, so I've split your post and alphaamanitin's reply off into its own thread.

Testdisk should only be used in certain circumstances. You might want to post details of why you are trying to use it so that forum members can advise you best.


lol, I didn't notice.  Reminds me of an xkcd comic.

AlphaA

---

