---
title: "&quot;Sharing Folder&quot; problem"
date: 2010-08-24
forum: General Help
---

### Post by Kaede393 on 2010-08-24
Hello.
I have a little big problem with the "Sharing Folder" option.
For you to know I use Ubuntu 10.04.
The problem is as follow:
Right clicking on a folder I can see many options and among them there is the "Sharing Folder".
Selecting that option I am able to share that specific folder with anyone and thats fine for the moment. Doing that I see two arrows on the folder's icon and other computers can access that folder without problem. Is all good. :)
When I close the user session or I do restart the computer, I login into the session and the folder seems to be not shared, at least thats what I can see because there are no arrows on the folder's icon, and if I check the "Sharing Folder" option the folder is not shared, like if I have done nothing. :(
The curious thing is other computers can access that folder even after restarting my box as if it is still shared, but I see it like not shared t all. :confused:
Maybe is a silly problem, but I have tried many ways to fix, reinstalling samba and all and is killing me!. :mad:
I will appreciate any help.
Thank you.

---

### Post by Morbius1 on 2010-08-24
There is a known bug that describes your predicament: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480)

The bug report implies that it's a problem with nautilus-share but the real problem is with nautilus itself. If you were to create a new folder and not use one of the default folders in your home directory and share that you might see that the share emblem survives a reboot.

In any event the only true way to determine what folders are shared ( and how they are shared ) is to look at the output of the following command:
```
net usershare info
```

---

### Post by Kaede393 on 2010-08-25
Thank you for the info, but somehow I fixed it... with a non technical solution. :)
Without login out from the user session I checked the share tag in the folder's properties, it was disable each time I checked and had to share the folder again, the curious thing is that the folder's icon didn't change while I was logged, but the sharing option in the folder's properties did. ](*,)
I did put the folder to be shared each time and somehow it stop happening. ](*,)
I have logged out and restart my computer and the folder is all fine like it have to be, with the sharing icon and the properties correctly set. :D

---

### Post by dtoronto on 2010-08-25
> **Morbius1 said:**
> There is a known bug that describes your predicament: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/280480)

The bug report implies that it's a problem with nautilus-share but the real problem is with nautilus itself. If you were to create a new folder and not use one of the default folders in your home directory and share that you might see that the share emblem survives a reboot.

In any event the only true way to determine what folders are shared ( and how they are shared ) is to look at the output of the following command:
```
net usershare info
```

on a side note, if I don't want to use nautilus at all to share, what is the proper way to set up a share folder named /folder using the CLI?

---

### Post by Morbius1 on 2010-08-25
dtoronto, not sure I understand the question.

There are two ways to create samba shares in linux. The one we're talking about in this thread is called Nautilus-share or "usershares" in samba. The whole idea is to use the file manager ( Nautilus or Thunar ) to create a share. However there is a way to create a userhare using the CLI.

Let's say I wanted to share my Pictures folder. I could create the share from the terminal this way:

> net usershare add pictures /home/morbius/Pictures "morbius pictures" everyone:F guest_ok=yThis will create a share named "pictures"
with a path = /home/morbius/Pictures
with the comment "morbius pictures"
with "Full" read / write access. ( Note: if you only want read access then modify the "everyone:F" to "everyone:R" )
with guest access allowed

The syntax is pretty strict so if , for example, you didn't want a comment you just can't leave it out. Instead you would change "morbius pictures" to "".

The alternative is to not use usershares but Classic-shares. THat would entail editing /etc/samba/smb.conf directly using vi / vim / nano or some other terminal based file editor. It's syntax would be different that what's used with userhsares.

---

