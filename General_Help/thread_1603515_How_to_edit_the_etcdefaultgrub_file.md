---
title: "How to edit the /etc/default/grub file?"
date: 2010-10-22
forum: General Help
---

### Post by bjnueva8623 on 2010-10-22
I've been using 10.04 for a few months without any problems, but today, I tried to boot into Ubuntu and just got a black screen. 

I tried the tutorial on _**[this site]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")**_, and it worked. 

The only problem is, I have to do this after every reboot unless I edit the **/etc/default/grub** file (the second part of the tutorial). I'm not sure how to go about doing this since the article is very vague. 

Any help would be much appreciated. Thanks.

---

### Post by sisco311 on 2010-10-22
Open a terminal (Applications -> Accessories -> Terminal) and run:
```
gksu gedit /etc/default/grub
```

You will be prompted for your password. Introduce it. The text editor will open the file. Edit it, save the changes(Ctrl+s), close it (Alt+F4),then run:
```
sudo update-grub
```
to generate a new grub2 config file.

---

### Post by drs305 on 2010-10-22
Here's a link to the 5 most common things you might change in Grub2:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by bjnueva8623 on 2010-10-22
Thanks a lot!

---

