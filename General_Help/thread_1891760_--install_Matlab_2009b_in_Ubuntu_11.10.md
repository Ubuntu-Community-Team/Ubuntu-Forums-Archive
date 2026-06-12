---
title: "--install Matlab 2009b in Ubuntu 11.10"
date: 2011-12-06
forum: General Help
---

### Post by minmin7 on 2011-12-06
Hello anyone can help me?
I`m new user in Ubuntu 11.10.I want to install Matlab 2009b linux ver.(iso).I googling and read about installion.But I can`t understand at all.So can anyone explain or show how to install matlab step by step.I`m noob in linux.Thanks for helping.:)

---

### Post by gennatolls on 2011-12-06
First read [THIS]("https://help.ubuntu.com/community/MATLAB")

You can refer to this guide for your icon and a proper place to install Matlab. The installer should be pretty simple and self explanatory 

**Note: I know this is for a newer version but 2009b is linked at the bottom


Now to mount your ISO file to run the installer.

In Terminal:
```


sudo su

mount -o loop /home/username/NAMEOFYOURISOFILEHERE.iso /mnt

cd /mnt

./install
```

Make sure you use the proper name of your iso and correct username.

LOL I'm not even going to ask how you acquired your ISO file and don't have the install DVD and the manual to install. :-\"

---

