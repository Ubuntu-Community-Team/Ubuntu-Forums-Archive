---
title: "'mv' command didn't perform like I expected..."
date: 2012-02-03
forum: General Help
---

### Post by Scooter_X on 2012-02-03
I just wanted to 'mv' a rom into a '.roms' folder in my home directory. I didn't have a '.roms' folder before I started. I was under the impression that once I:

```
mv zeldahackedrom.smc /home/riley/.roms 
```

then it would create the '.roms' folder for me and stuff zeldahackedrom.smc into it.

However, even though 'ls -a' showed me that it was indeed in the home folder, if I tried 'cd .roms' it told me 'bash: cd: .roms: Not a directory'. Also, I couldn't see it in nautilus, but I did see all the other hidden files. 

So, I tried creating the directory (mkdir .roms) and it said "sorry, that's already a directory". So I removed it, did the 'mkdir .roms' thing, then moved the .smc into it and it works now.

Any reasons why it wouldn't have worked the first time around? Has anyone had the same problem happen to them when trying to move files into a non previously existing folder?

---

### Post by WorMzy on 2012-02-03
Your command will move _and rename_ the file if the .roms folder doesn't exist.

```
man mv
```

---

### Post by papibe on 2012-02-03
When the destination (2nd argument) is not a directory, mv works as 'move and rename'.

In your case, your file was not only moved to /home/riley/, but also renamed to .rom

BTW, you can see hidden folder and files (start with a dot) on Nautilus, by pressing Ctrl+H.

Hope it helps.
Regards

---

### Post by Scooter_X on 2012-02-03
Aaaaah, duh. It shoulda been: 
```
mv thefile.smc /home/riley/.roms/thefile.smc
```

Thanks guys

---

