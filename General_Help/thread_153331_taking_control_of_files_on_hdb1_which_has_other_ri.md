---
title: "taking control of files on hdb1 which has other rieserfs"
date: 2006-03-31
forum: General Help
---

### Post by frup on 2006-03-31
i screwed up my grub on linspire installing ubuntu. and cant get in to linspire now.
the drive is mounted in ubuntu and i can see all the files... some i can open but most i can't, i dont have the permissions to.

how do i take ownership of these files so i can copy them to hda1 and reinstall linspire?

thanks for any help :)

---

### Post by Ramses de Norre on 2006-03-31
Don't know whether it's the same on reiserfs but try: ```
sudo chown -R your_username mountpoint
```

---

### Post by frup on 2006-03-31
[QUOTE=Ramses de Norre]Don't know whether it's the same on reiserfs but try: ```
sudo chown -R your_username mountpoint
```[/QUOTE]


i cd .. twice out of home 
then:
laurent@ubuntu:/$ sudo chown -R laurent /Linspire
files all the same but it replied no error.

at first (when i started typing) i thought it didnt work. but i just tried once more and i found it just took a while to own all 33 GB :D so i got ownership now which is great. 

thanks :D

which i could do it GUI... bit faster

---

