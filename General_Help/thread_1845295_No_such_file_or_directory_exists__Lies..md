---
title: "No such file or directory exists?  Lies."
date: 2011-09-16
forum: General Help
---

### Post by a_movingtarget on 2011-09-16
Alright.  I've been sitting here for a while now trying to delete some files from my Music folder that are not actually musicfiles, how they got there (I know...) I have no idea.  I've tried the whole rm -f, /home/music/SK\ iTunes_files   command, I've tried it without the -f, without the /home/music, etc....  I have gotten a file to move after much trying (once again, not really sure what I did when it worked. wtf do I need to type into this command line to delete these files?  It always says that no such file or directory exists, but when I look in the folder, there it is.  Please help me, I beg you gurus (or anyone)!  Thanks. I'll owe you a beer.

---

### Post by TeoBigusGeekus on 2011-09-16
There has to be your username between /home and /music, ie.
```
rm /home/yourusername/music/etc...
```

---

### Post by theanimalbaetista on 2011-09-16
If I'm reading this correct you try 

>  cd ~
sudo rm -rf "music folder to delete" 

---

### Post by oldos2er on 2011-09-16
I think you'd need to try /home/user/Music/SK\ iTunes_files/*
Linux is case-sensitive, and the Tab completion key is your friend.

---

