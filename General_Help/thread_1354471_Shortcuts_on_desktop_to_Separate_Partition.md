---
title: "Shortcuts on desktop to Separate Partition"
date: 2009-12-13
forum: General Help
---

### Post by zbirdman777 on 2009-12-13
Hey guys! Just wondering if you can tell me how to create shortcuts on my desktop and home folder to folders in a separate partition. When I try to make a link it says 'Operation not Permitted'. 

It's a fat32/vFat format partition that is mounted at startup.

---

### Post by pastalavista on 2009-12-13
Just right-click on the desktop, 'create launcher' select type 'location' and enter the full path. It creates a symbolic link (symlink) which will look like a folder with an arrow on it but works just like a shortcut.

---

### Post by lmarmisa on 2009-12-13
Try to define a symbolic link.

```

ln -s target link_name

```
Best regards,

Luis

---

### Post by zbirdman777 on 2009-12-14
Neither way worked. The symbolic link gave exactly the same error that said 'Operation Not Permitted'.

The launcher said file type not supported. I chose 'Location' as the option.

However when I was trying the launcher it allowed me to add shortcuts to 'Places' at the top left, but only 2 folders appeared in my Home folder, Documents and Games. 

My other folders (Pictures, Videos, Music) didn't appear in my home folder for some odd reason. So I can make a link to 'Documents' and 'Games' but not the others. Very strange...

---

### Post by dcstar on 2009-12-14
> **zbirdman777 said:**
> Hey guys! Just wondering if you can tell me how to create shortcuts on my desktop and home folder to folders in a separate partition. When I try to make a link it says 'Operation not Permitted'. 

It's a fat32/vFat format partition that is mounted at startup.

You cannot make links to primitive filesystems like FAT32.

---

### Post by lmarmisa on 2009-12-14
I have checked that symbolic lynks to NTFS work OK. I have the ntfs3g package.

---

### Post by zbirdman777 on 2009-12-14
> **dcstar said:**
> You cannot make links to primitive filesystems like FAT32.

Ahh. This would be a problem. lol. I chose fat32 because it worked well between my Ubuntu and Vista dual boot. I could easily change the filesystem format however. Is there a recommendation? I want to stay away from NTFS though.

---

### Post by lmarmisa on 2009-12-14
I prefer NTFS than fat32. My recommendation is: forget fat32.

---

### Post by mikewhatever on 2009-12-14
> **zbirdman777 said:**
> ............

My other folders (Pictures, Videos, Music) didn't appear in my home folder for some odd reason. So I can make a link to 'Documents' and 'Games' but not the others. Very strange...

How is that possible? Pictures, Videos and Music should be in your home folder by default, and no shortcuts should be needed. If they aren't, where are they then? Can you post the output of <ls> to verify that.

---

### Post by zbirdman777 on 2009-12-14
> **mikewhatever said:**
> How is that possible? Pictures, Videos and Music should be in your home folder by default, and no shortcuts should be needed. If they aren't, where are they then? Can you post the output of <ls> to verify that.

Let me explain. I don't have Documents, Music, or etc in my home folder because I deleted them. Since I dual boot, I keep all of my files on 1 partition dedicated to storage so Documents, Music, etc is the same for both OS. I replaced those folders in vista with shortcuts to the folders in the fat32 partition I was talking about. That's what I was trying to do in Ubuntu.

I'll try ntfs I suppose. Thanks for the help guys!:D

---

