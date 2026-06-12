---
title: "NTFS partition problem"
date: 2010-03-30
forum: General Help
---

### Post by claudiogbr on 2010-03-30
hi, i have a netbook configured with 3 partition:
1. ntfs - win7 ultimate (70 gb)
2. (a big) ntfs called media (200gb i think)
3. ubuntu 9.10 (50 gb)

it was running ok but i saved on the ntfs partition from linux a folder with some photos on the ntfs(media) part, 
after this i restarted the pc and entered with win7 (from hibernation) and used only nokia pc suite i think, maybe i've done some upgrade but never entered in the ntfs(media) partition, finished my nokia backup i re-hibernate win7 and reopen ubuntu
surprise, the folder with the photos disappeared,and also a folder i've created with all the pdf i have disappeared. So i've tryed to re enter in win7 but nothing new, all the file created or modified from ubuntu was deleted, this include all the file at all, documents, mp3, avi. I've tryed to recover the files but the space was owerwritten with win7 system files. i don't know if it is a bug of win7 or ubuntu but be careful if you have important file on an ntfs part.

hope that all is clear, if not tell me, i'll try to explain better
(pc is samsung nc10 with wd 320g hd)

---

### Post by byStanderone on 2010-03-30
...is ntfsprogs installed in your ubuntu? it is needed by ubuntu karmic for it to be able to handle ntfs.

---

### Post by claudiogbr on 2010-03-30
no, i have 
ntfs-3g and libntfs10
do you think i can resolve with ntfsprogs?

---

### Post by ajgreeny on 2010-03-30
Was the win7 in hibernation when you booted to ubuntu and saved your photos onto the NTFS partition?

Firstly, I would have expected that it was not possible to mount the NTFS partition if it was hibernated, as it would still be flagged as "in use" by the win file system.

Secondly, if you force mounted the NTFS partition, you may have caused problems in the win file system by mounting it and then writing to it when it was in effect still being used.

Whether a chkdisk from windows of that NTFS partition will sort out the problem, I'm not sure, but it must be worth trying.  This may provide a salutary lesson in how not to use hibernation in a dual boot system, if what I suggest is what happened, and I am sorry I can not offer any other ideas for you.

---

### Post by claudiogbr on 2010-04-02
you are wrong, win7 partition and the media ntfs partition are diffent, and win7 delete all the data in the media ntfs partition and not in the ntfs win7 system partition where i never do anything from ubuntu

---

### Post by byStanderone on 2010-04-02
well, i hope you've solved your problem by now...installing ntfsprogs won't hurt your system, and since you have an ntfs partition...i'd say you need it.

---

### Post by claudiogbr on 2010-04-02
yes thanks, ntfsprogs solved the question, i don't understand why it's not installed by default in ubuntu, it can cause a really big data loss problem.....

---

