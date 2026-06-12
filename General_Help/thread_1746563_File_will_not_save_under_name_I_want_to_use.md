---
title: "File will not save under name I want to use"
date: 2011-05-01
forum: General Help
---

### Post by Silvernail on 2011-05-01
I am have problems with: gedit, abiword, mv, cp, touch, and rename.
The text file was created with 'gedit' and save out of frustration with the title of 'Unsaved Document 1'.

I now wish to give it a name and save it.
'gedit' and 'abiword' will not save it with the name "Annie Street Arts Collective Play List 5/11", they will save it as 'Unsaved Document 1'. 
gedit' has work flawlessly for me up until this incident.

I've never run into this before, I don't know what to start looking for. What do I look for to fix what is broken?

dave@dave:/media/seagate_/AnnieStreet$ id
uid=1000(dave) gid=1000(dave) groups=4(adm),20(dialout),24(cdrom),44(video),46(plugdev),104(lpadmin),115(admin),120(sambashare),1000(dave)


```
dave@dave:/media/seagate_/AnnieStreet$ cp "Unsaved Document 1" "Annie Street Arts Collective Play List 5/11"
cp: cannot create regular file `Annie Street Arts Collective Play List 5/11': No such file or directory

dave@dave:/media/seagate_/AnnieStreet$ mv "Unsaved Document 1" "Annie Street Arts Collective Play List 5/11"
mv: cannot move `Unsaved Document 1' to `Annie Street Arts Collective Play List 5/11': No such file or directory

dave@dave:/media/seagate_/AnnieStreet$ touch "Annie Street Arts Collective Play List 5/11"
touch: cannot touch `Annie Street Arts Collective Play List 5/11': No such file or directory

dave@dave:/media/seagate_/AnnieStreet$ rename "Unsaved Document 1" "Annie Street Arts Collective Play List 5/11"
Can't locate object method "Unsaved" via package "Document" (perhaps you forgot to load "Document"?) at (eval 1) line 1.
```

Thanks for any help you can provide.
Dave

---

### Post by Bucky Ball on 2011-05-01
Don't think you can use /. Try without (perhaps with - or _ instead). Also, not sure if there is a limit on the number of characters you can use; maybe you are over it.

---

### Post by Silvernail on 2011-05-01
> **Bucky Ball said:**
> Don't think you can use /. Try without (perhaps with - or _ instead). Also, not sure if there is a limit on the number of characters you can use; maybe you are over it.
I feel so dumb I'm just going to bed and treat myself to a nightmare.

Of course it was looking for a directory named '5'.
Thanks for catching that.
Dave

---

### Post by Bucky Ball on 2011-05-02
> **Silvernail said:**
> I feel so dumb I'm just going to bed and treat myself to a nightmare.

Haha. That's funny! Enjoy the nightmare. Don't worry, these things happen to us all now and then ... ;)

---

