---
title: "I cannot access my /root folder"
date: 2012-05-20
forum: General Help
---

### Post by staticjess on 2012-05-20
I originally had a problem with my linux which was a elf grub rescue error. I followed a couple of advices but my linux ended up with a blank screen. I tried to access my files via ubuntu live CD and they are still there intact. I already backed up all my files from my Windows (Ubuntu & Windows Dual Boot) but some of the files from my /home folder and all the files in my /root folder have permission issues. i pretty much given up on fixing the previous grub error, I tried reinstalling grub, repairing my system and I cannot fix is anymore. So my solution is to back everything up and reinstall my ubuntu and my windows. 

As you can see, I am new at ubuntu and I need the community's help on this. All I want is to retrieve my files from home and root folder. By the way I asked for a solution for this in other forums and all they can so is scold me about why I placed a private file on my /root folder. I know I shouldn't and there's nothing I can do now. I need a solution guys, help anyone?

---

### Post by staticjess on 2012-05-20
I don't know much about linux commands yet, can anyone guide me so I can backup my files to my external hard drive? Thanks in advance

---

### Post by CatKiller on 2012-05-20
```
 gksudo nautilus
``` from a live cd will run a file browser as root. This will let you sort out those files.

If you don't muck about as root so much on your next install you won't end up with permissions problems on files in your Home folder, nor with your files in root's Home folder.

---

### Post by Dave_L on 2012-05-20
(duplicate info, please ignore this)

---

