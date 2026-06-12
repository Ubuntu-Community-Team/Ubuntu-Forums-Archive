---
title: "lost files"
date: 2010-09-19
forum: General Help
---

### Post by mikecahill on 2010-09-19
My grand daughters computer (xp) was running slow due to a) the OS and b) the rubbish she had downloaded, so I copied all her photos, vids  and music onto an ipod type thing, while i reinstalled xp when I transfered them back, they are all corrupted, the file names now look like the name of the Greek prime minister, and nothing I've tried even recognises them as media files. I tried to move them to a folder on my ubuntu computer, and they didn't transfer, but they have disapeared from the ipod thing too. please tell me they are still there, just hidden and there is a linux workaround that will make them reappear, and one that will enable me to recover them, or I am in deep Do Do's. Any advice is welcome, but please keep it simple, and give step by step instructions. and don't tell the grand daughter !!)
cheers
Mike

---

### Post by bluefrog on 2010-09-19
using  a ubuntu "live" cd, you could boot on your XP computer (as live ubuntu obviously) and get the pictures back on IPOD or transfer them from the live session to your existing ubuntu.

---

### Post by Serpher on 2010-09-19
You're going to want to run the command:

```
sudo strings /dev/sdb1 > ~/Desktop/iPod\ Files
```

sdb1 might be sdc1 etc etc. The command 'ls /dev/|grep sd??' might help you figure out which one is the iPod.

This will pull all the raw binary data out of the iPod, and into a file on your Desktop callled 'iPod Files'. Open the file and look for a group of sections that look like they're pictures. The headings of the sections might help you as they might contain the file names or if it's a jpg or something. Copy paste a whole section into Applications --> Text Editor (gedit), And save it as a .jpg or whatever format the picture was in. Keep doing this until you have all the pictures back.

---

