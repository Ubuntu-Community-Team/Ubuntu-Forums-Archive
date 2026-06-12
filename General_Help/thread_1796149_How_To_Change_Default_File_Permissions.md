---
title: "How To Change Default File Permissions"
date: 2011-07-03
forum: General Help
---

### Post by haon8 on 2011-07-03
Hey everyone, my dad has been using Ubuntu for a few weeks now and likes it, however he's having some issues regarding read-only files. He's a doctor and frequently has to download word files to edit, however they always download as a read-only file. While this isn't particularly difficult to do, he finds doing it tiresome and because he isn't the most proficient PC user, may have difficulty with it when I return to school after the summer. I was hoping that there's some way to change the default settings so that all files downloaded are writeable.

Additionally, he has a number CD-RWs which he both retrieves files from and stores them to, however when trying to access these CDs he is told that they are read-only. Right clicking on the CD and trying to change the access permissions doesn't work (says that permissions can't be changed because the disc is read-only). Help is appreciated!

---

### Post by raja.genupula on 2011-07-03
hey man  if you change that file permissions then you can do it what ever you want 


              just try ```
sudo chmod 777 file_path
```

---

### Post by haon8 on 2011-07-03
> **raja.genupula said:**
> hey man  if you change that file permissions then you can do it what ever you want 


              just try ```
sudo chmod 777 file_path
```

Uhh...sorry? I don't really understand what you're saying. When I try typing that in in the terminal it tells me something about my dad's password, but won't let me type anything in.

---

### Post by Habitual on 2011-07-03
> **haon8 said:**
> ....Right clicking on the CD and trying to change the access permissions doesn't work (says that permissions can't be changed because the disc is read-only)...

The "RO" in CDROM stands for Read-Only.

Copy them off the CDROM then change the perms.

---

### Post by haon8 on 2011-07-03
> **Habitual said:**
> The "RO" in CDROM stands for Read-Only.

Copy them off the CDROM then change the perms.

It's not a CD-ROM, it's a CD-RW. It's meant for storage and whatnot. Either way, the problem is that I can't copy files to the CD because it tells me that the media is read-only.

---

### Post by haon8 on 2011-07-04
Anybody? This is a pretty big issue.

---

### Post by xrhettx on 2011-07-04
Hi. Don't use chmod 777. It doesn't sound like you're experienced enough to not damage the computer. Don't take it personally; chmod is a very powerful command. I want to teach you about file permissions but you'll have to read up on them. They're really important. 
Here are some links I found useful during my studies of file permissions:
[http://www.washington.edu/computing/unix/permissions.html](http://www.washington.edu/computing/unix/permissions.html)
[google_search]("http://www.google.com/search?client=ubuntu&channel=fs&q=linux+bible+study&ie=utf-8&oe=utf-8#hl=en&sugexp=gsihc&pq=linux%20ntfs&xhr=t&q=ubuntu+file+permissions&cp=14&qe=dWJ1bnR1IGZpbGUgcGU&qesig=ZxpvwOt2TleYTrkmKYHqfQ&pkc=AFgZ2tntapU4-d3ZSAD7E2OCCQ-DW1XInsjrlkgcMUfUhdsAb2ydXqMqnO4xWx9vOCVVEqeIra6Kx6Lq9sWfy6-wiRH7mIPsFA&pf=p&sclient=psy&client=ubuntu&channel=fs&source=hp&aq=0&aqi=&aql=f&oq=ubuntu+file+pe&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=1ec92a21f3882047&biw=1680&bih=823")

Although I suggest learning about aforementioned file perms., it doesn't sound like they are your problem. When your father downloads a file, they're probably going to a /tmp folder (temporary folder with read only access, whose permissions you do not change ). So whatever location the files are being downloaded from, say an Internet browser like firefox, the Download preferences should be changed from that application. If they're from a non-writable removable media like a CD-R, copy them to a folder in your home/user_name/Documents directory.  The file permissions in a users /Documents folder differs from the /tmp folder; the /tmp folder is owned by root, the Doc folder by the user; and so the user can edit/write the files in his Doc folder and not in the /tmp folder.
Rather lengthy but I hope this helps. Msg with any questions!

---

### Post by haon8 on 2011-07-04
> **xrhettx said:**
> Hi. Don't use chmod 777. It doesn't sound like you're experienced enough to not damage the computer. Don't take it personally; chmod is a very powerful command. I want to teach you about file permissions but you'll have to read up on them. They're really important. 
Here are some links I found useful during my studies of file permissions:
[http://www.washington.edu/computing/unix/permissions.html](http://www.washington.edu/computing/unix/permissions.html)
[google_search]("http://www.google.com/search?client=ubuntu&channel=fs&q=linux+bible+study&ie=utf-8&oe=utf-8#hl=en&sugexp=gsihc&pq=linux%20ntfs&xhr=t&q=ubuntu+file+permissions&cp=14&qe=dWJ1bnR1IGZpbGUgcGU&qesig=ZxpvwOt2TleYTrkmKYHqfQ&pkc=AFgZ2tntapU4-d3ZSAD7E2OCCQ-DW1XInsjrlkgcMUfUhdsAb2ydXqMqnO4xWx9vOCVVEqeIra6Kx6Lq9sWfy6-wiRH7mIPsFA&pf=p&sclient=psy&client=ubuntu&channel=fs&source=hp&aq=0&aqi=&aql=f&oq=ubuntu+file+pe&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=1ec92a21f3882047&biw=1680&bih=823")

Although I suggest learning about aforementioned file perms., it doesn't sound like they are your problem. When your father downloads a file, they're probably going to a /tmp folder (temporary folder with read only access, whose permissions you do not change ). So whatever location the files are being downloaded from, say an Internet browser like firefox, the Download preferences should be changed from that application. If they're from a non-writable removable media like a CD-R, copy them to a folder in your home/user_name/Documents directory.  The file permissions in a users /Documents folder differs from the /tmp folder; the /tmp folder is owned by root, the Doc folder by the user; and so the user can edit/write the files in his Doc folder and not in the /tmp folder.
Rather lengthy but I hope this helps. Msg with any questions!

It's not an issue where the files are uploaded from; when my dad was downloading them while he was still using Windows he never had any issues. And the files download to the "Downloads" folder. Do you have any suggestions on how to fix the issue with getting files onto the CD-RWs?

---

