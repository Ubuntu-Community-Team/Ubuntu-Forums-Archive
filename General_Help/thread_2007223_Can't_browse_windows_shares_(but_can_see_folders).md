---
title: "Can't browse windows shares (but can see folders)"
date: 2012-06-20
forum: General Help
---

### Post by bennettg on 2012-06-20
hello. I am a noob in search of help.

I have an old dell laptop that now functions as a sever with ubuntu 110.4 on it, with samba. 

On a newer laptop, i just installed ubuntu 12.04 fresh (not upgrade). when I use nautilus to browse the network, i can see the old dell (called jdsip) and even see the folders that are supposed to be shared. however, when i click on one of the folders to try to see contents, i get an error message:


Unable to mount location: Failed to Mount Windows Share

I find this odd, because I can access those files/folders on the old dell with android and ipad. 


i studied different threads that seemed related and could not solve the problem. any ideas?

thanks in advance.

---

### Post by Ambimom on 2012-06-20
I had the same problem,  My laptop is almost 10 years old and my 64-bit Windows 7 desktop is just barely a year old.  In an effort to speed up the laptop, I loaded Ubuntu 12.04 onto it.  When I first tried to network the two of them, they could see each other but neither could access the files in the other one.

This is how I solved it.

[http://www.liberiangeek.net/2010/09/quickly-access-windows-shares-ubuntu-10-10-maverick-meerkat/]("http://www.liberiangeek.net/2010/09/quickly-access-windows-shares-ubuntu-10-10-maverick-meerkat/")

Combined with...

[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7]("http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7")

Now I can share info and read/write files in both directions.

Good luck!

---

### Post by Morbius1 on 2012-06-20
>  Unable to mount location: Failed to Mount Windows ShareYou will note that it's telling you that it can't mount it not that it can't find it. This is usually not a Samba problem but a Linux permissions problem on the folder you are trying to share.

If you provide the following information many here can help you diagnose the problem:
```
testparm -s
``````
net usershare info --long
```

---

### Post by bennettg on 2012-06-20
> **Morbius1 said:**
> You will note that it's telling you that it can't mount it not that it can't find it. This is usually not a Samba problem but a Linux permissions problem on the folder you are trying to share.

If you provide the following information many here can help you diagnose the problem:
```
testparm -s
``````
net usershare info --long
```

Will do so.....On which computer....the server or the client?  If the server has permission problems, would you expect access problems on other devices?  I do not have problems seeing and accessing server folders and files with iPad Android etc.

Will post output shortly and greatly appreciate
the help.

---

### Post by Morbius1 on 2012-06-21
Those commands are to be done on the server.

---

