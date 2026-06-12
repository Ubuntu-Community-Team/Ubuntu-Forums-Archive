---
title: "How to back up my whole system?"
date: 2009-09-17
forum: General Help
---

### Post by rock it on 2009-09-17
Hey all,
Is there a way for me to back up my whole system onto dvds?
Beacause it's onto dvd's Ill need a way to split the backup, is there a way to do this?

Thanks

---

### Post by NightwishFan on 2009-09-17
What are you trying to back up? You can use compress tar files to back up directories. If you want a "system restore" I am not sure one exists, but someone might know around here.'

My advise is to keep a seperate partition for data to begin with, that way you keep all your personal data if you need to reinstall.

---

### Post by yanceypd on 2009-09-17
Clonezilla will creat a ghost type image.  Not sure if will do it to a cd but will to jump drive.

---

### Post by rock it on 2009-09-17
> **NightwishFan said:**
> What are you trying to back up? You can use compress tar files to back up directories. If you want a "system restore" I am not sure one exists, but someone might know around here.'

My advise is to keep a seperate partition for data to begin with, that way you keep all your personal data if you need to reinstall.

I realize this might sound strange but the thing I want to backup is programs (I really don't want to have to download and install all my programs again) I dont really have many files, about 1gb music and that's it. Also Im new to linux and I am not sure what TAR is? :confused:

---

### Post by NightwishFan on 2009-09-17
Use APTONCD. It will take all the extra programs you installed an make them into an installable CD.

```
sudo apt-get install aptoncd
```

Make sure if you have 32-bit programs use 32-bit ubuntu. Backing up will not work from 32 to 64-bit

[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

Got to go man, sorry, and good luck! :guitar:

---

### Post by rock it on 2009-09-17
> **NightwishFan said:**
> Use APTONCD. It will take all the extra programs you installed an make them into an installable CD.

```
sudo apt-get install aptoncd
```Make sure if you have 32-bit programs use 32-bit ubuntu. Backing up will not work from 32 to 64-bit

[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

Got to go man, sorry, and good luck! :guitar:
ciao.

If anyone can help?
I installed APTONCD but when I open it up and and "create" the bar loads to 90% then crashes??? I checked the terminal and it says something about being "unable to fork". Any ideas? I'll have a browse about and see if I can find an answer.

---

### Post by rock it on 2009-09-17
> **rock it said:**
> ciao.

If anyone can help?
I installed APTONCD but when I open it up and and "create" the bar loads to 90% then crashes??? I checked the terminal and it says something about being "unable to fork". Any ideas? I'll have a browse about and see if I can find an answer.

ok aptoncd seems to be working will try out tomorrow, will keep updated

---

### Post by OrionDarion on 2009-10-08
And? Did it work? I want to try it also.

---

### Post by Kegusa on 2009-10-08
Yeah, did it work? By the lack of response this was what the OP was looking for, I'm heavy on modifying my system at all times so this might be something for me too :)

Anyone with good testimonials? And also will it work with non-synaptic installed software?

---

### Post by NightwishFan on 2009-10-09
It only works on Debian packages, I believe. I have personally tried it, and currently use it. The only bug I have found was that it uses RAM to load the package database, so if you use a lot of packages the program may crash. Hopefully they fix that in the future. It does work, though.

However please note! If you ever cleared the apt-cache you are going to have to redownload all the package files. It does not redebianize installed packages, just copies from the cache. You can choose to "download only" packages in Synaptic. That is a godsend.

---

