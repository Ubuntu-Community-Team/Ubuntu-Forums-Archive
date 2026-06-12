---
title: "Home directory does not appear to exist"
date: 2009-07-15
forum: General Help
---

### Post by bboston7 on 2009-07-15
I followed the directions on this page ([https://wiki.edubuntu.org/EncryptedHomeFolder](https://wiki.edubuntu.org/EncryptedHomeFolder)) and now when I try to log in, I get the error message ```
"Your home directory is listed as: '/home/brett' but it does not appear to exist/  Do you want to log in with the / directory as your home directiory? ..."
```

When I use Ctrl+Alt+F1 and try to cd into my directory it says "Permission Denied".

I have tried to chown the directory to brett:brett as well as chmod it to 644 but I still run into the same problems.

Thank you in advanced for your help.

---

### Post by bboston7 on 2009-07-15
could I fix the problem if I
```
rmdir /home/brett
mv /home/brett.bak /home/brett
```

---

### Post by lisati on 2009-07-15
> **bboston7 said:**
> could I fix the problem if I
```
rmdir /home/brett
mv /home/brett.bak /home/brett
```

Only if a folder brett.bak exists and if it has the correct permissions. It might be easier to do a rmdir then a mkdir then a cp from the backup folder.

---

### Post by bboston7 on 2009-07-15
> **lisati said:**
> Only if a folder brett.bak exists and if it has the correct permissions. It might be easier to do a rmdir then a mkdir then a cp from the backup folder.
The backup folder does have the correct permissions and it will let me rmdir /home/brett, but I still cant do anything with that filepath whatsoever.

Since I have the backup folder, I think I'm going to do a reinstall with the alternate cd so I can encrypt my home directory and just move all my files back after the reinstall. 

The only question I have now is, will my settings be preserved when I move all of my data back?

---

