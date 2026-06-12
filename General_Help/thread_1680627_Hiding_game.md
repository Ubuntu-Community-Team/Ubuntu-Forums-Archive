---
title: "Hiding game"
date: 2011-02-02
forum: General Help
---

### Post by Arihiza on 2011-02-02
Hey, I am new to ubuntu and yesterday I tried installing BFBC2 in wine. It installed fine but then I found out that Ubuntu doesn't support punkbuster, so I was like "ok" and went to uninstall it.

Now, the thing is I cannot find it. I think I noobed out and ran wine in root when I installed it. I can find the shortcut for the game if I go into root/desktop. The command for the shortcut is ```
env WINEPREFIX="/root/.wine" wine C:\\Program\ Files\\Electronic\ Arts\\Battlefield\ Bad\ Company\ 2\\BFBC2Updater.exe 
```.

When I search in C:\\.... the game is not there. I have even tried opening it in root, still can't see it. I know the game is installed, because it will run, but it is totally hidden.

So yeah, if anyone knows how I can fix my noob mistake that would be awesome.

Thanks.

---

### Post by Arihiza on 2011-02-03
Oh, I have also tried reaching the folder using terminal. Couldn't find it. Even root terminal couldn't.

---

### Post by Arihiza on 2011-02-03
Bump. Anyone know what's going on here?

---

### Post by 23meg on 2011-02-03
Hey, Arihiza.

Send me a private message with more details and I will see what I can do for you.

Thanks,
Meg.

---

### Post by mastablasta on 2011-02-03
> **Arihiza said:**
>  
When I search in C:\\.... .
 
what C:\\ ? there is no C:\\ in linux.
 
have you checked in home\.wine folder? if you can't see it in nautilus press ctrl+h.

---

### Post by howefield on 2011-02-03
Hi Arihiza

Have you tried the suggestions on this page ?

```
https://help.ubuntu.com/community/Wine#Uninstalling Wine Applications
```

---

### Post by LoneWolfJack on 2011-02-03
if you installed as root, the game should be in /home/root/.wine/drive_c

---

### Post by Arihiza on 2011-02-03
> **LoneWolfJack said:**
> if you installed as root, the game should be in /home/root/.wine/drive_c
Damn, there it is. I... didn't see that place. Even when I was opening up root I was going into the normal .wine folder... Told you I was noob :)

Thanks XD

---

