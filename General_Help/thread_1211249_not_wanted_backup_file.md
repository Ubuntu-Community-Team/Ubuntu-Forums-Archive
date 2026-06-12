---
title: "not wanted backup file"
date: 2009-07-12
forum: General Help
---

### Post by skyjacker on 2009-07-12
I made a backup file using info from this post > [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087), and it took ALL of my /partition space. I would like to remove it, but don't know how. Can I use an su command in terminal perhaps? Please help, I need my space back.
Thanks.  
Now I can't even use synaptic because itgives this error message.
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by cariboo on 2009-07-12
You can nautilus as root to rmove your unwanted backup file. Press Alt-F2 and type:

```
gksu nautilus
```

Then navigae to the unwanted backup file and send it to trash, then empty trash. I have delete enabled in nautilus, so I don't need the extra step of emptying the trash. Go to Edit-->Preferences-->Behaviour and enable it.

---

### Post by Aboelnour on 2009-07-12
peace upon you:
i have the same problem but i removed the backup file but the space still full 
i guess u can delete it by become root and delete it

---

### Post by skyjacker on 2009-07-12
> **cariboo907 said:**
> You can nautilus as root to rmove your unwanted backup file. Press Alt-F2 and type:

```
gksu nautilus
```

Then navigae to the unwanted backup file and send it to trash, then empty trash. I have delete enabled in nautilus, so I don't need the extra step of emptying the trash. Go to Edit-->Preferences-->Behaviour and enable it. I did this and still have my / space full. How else can I free up this space???

---

### Post by Aboelnour on 2009-07-12
i also used nautilus command to remove it but i don't free this space

---

### Post by skyjacker on 2009-07-12
> **Aboelnour said:**
> i also used nautilus command to remove it but i don't free this space Here is the answer "https://help.ubuntu.com/community/RecoverLostDiskSpace". I used the gksudo method. Good luck

---

### Post by Aboelnour on 2009-07-12
> **skyjacker said:**
> Here is the answer "https://help.ubuntu.com/community/RecoverLostDiskSpace". I used the gksudo method. Good luck
thanks

---

