---
title: "Read/Write privileges"
date: 2010-11-14
forum: General Help
---

### Post by pedroazenham on 2010-11-14
Hello,
 

 I have a pc with ubuntu 10.04 instaled, and a fold shared on my user directory.
 Witch are the permicions that i have to edit, so every time i create or edit a document (any tipe: openoffice,...), that document cam have read and write privileges on another computer in my home network so i can work on it?


Thankyou so much for any help given

---

### Post by JC Cheloven on 2010-11-14
All you need is to right click in the folder containing the docs you want to edit, select "sharing options", tick "share this folder", and tick "allow other users to write in this folder".

Then click "modify sharing". That should be it.

---

### Post by pedroazenham on 2010-11-15
Thankyou Cheloven for the reply, but it's not so simple...
With windows computers on the network, i have to use samba server!
I will search more information and when it's solved i post it here.

Thankyou

---

### Post by Morbius1 on 2010-11-15
> **JC Cheloven said:**
> All you need is to right click in the folder containing the docs you want to edit, select "sharing options", tick "share this folder", and tick "allow other users to write in this folder".

Then click "modify sharing". That should be it.

pedroazenham, The procedure described above is Samba. It's called Usershares and has been part of Samba for years.

---

### Post by Morbius1 on 2010-11-15
I reread your original post. I think you are using classic shares so why not post the output of the following command so we can see how you are set up:
```
testparm -s
```

---

### Post by JC Cheloven on 2010-11-15
> **pedroazenham said:**
> Thankyou Cheloven for the reply, but it's not so simple...
With windows computers on the network, i have to use samba server!
I will search more information and when it's solved i post it here.
Thankyou

As Morbius said, and weird it may be considered, the default sharing method in ubuntu is samba, not some linux-specific method. So it should work, remote editing of documents included. It works for me, although I use only ubuntu machines.

It comes to mind..., it's a shot in the dark but anyway: 
I'm not sure if trying to edit from win2 a document stored in a linux type of partiton (ext3 and the like) may lead to problems. It doesn't recognize such filesystems by default though.

---

### Post by pedroazenham on 2010-11-16
p { margin-bottom: 0.21cm; }  Hello guys,
 

 There is nothing wrong with my shared folder with samba, i can see and access my folder and edit documents on a windows PC.
 The problem is every time i create a new document on my linux PC, that document can be open only on read mode on another pc.
 

 I solved the problem with the umask:
 went to /etc/Pam.d/common-session and added this line
 session optional pam_umask.so umask=001
 

 then went to /etc/profile and commented (with a #) the line
 UMASK 002
 

 With this solution, every document created on my linux PC add the permissions given by the umask selected (owner= rwx; group=rwx; other=rw)
 For more information please search for umask permissions on google.
 

 Thank you all for the help given

---

