---
title: "Need help getting graphical interface back"
date: 2010-02-25
forum: General Help
---

### Post by hacc on 2010-02-25
Hi, ive edited my xorg and now when i start up ubuntu I cannot see the login interface, need help getting into safe mode or something to fix this issue.

hacc

---

### Post by NightwishFan on 2010-02-25
Hold in shift when you boot to access a menu. You can boot into recovery mode from there. To repair your Xorg.conf, choose Root Shell, and type this command:

```
cp /etc/x11/xorg.conf /etc/x11/xorg.conf.backup && nano /etc/x11/xorg.conf
```

This will backup your current xorg.conf, and let you open it to repair the damage. If you are on Karmic, you might just be able to "delete" it, as X can run without a Xorg.conf. Make sure you back it up if you attempt that.

---

### Post by hacc on 2010-02-25
Ok, I was able to get to the recovery mode command prompt but now its telling me cannot stat '/ect/x11/xorg.conf' : No such file or directory.

thanks,
hacc

---

### Post by NightwishFan on 2010-02-25
You need /**etc**/x11/xorg.conf

---

### Post by hacc on 2010-02-25
Sorry, that was a typo in the forum, I did type it that way and im still having the problem.

thanks
hacc

---

### Post by NightwishFan on 2010-02-25
I apologize, the X11 is meant to be capitalized.. I think a particular Nightwishfan needs some coffee.. ](*,)

```
/etc/**X11**/xorg.conf
```

---

### Post by hacc on 2010-02-25
Hmm, now its saying cannot create regular file 'etc/X11/xorg.conf.backup' : No such file or directory.

thanks
hacc

---

### Post by NightwishFan on 2010-02-25
Works for me, are you sure you have a xorg.conf? To make sure post the output of:
```
ls /etc/X11/ | grep xorg
```

Sorry to say I am not an expert on this. I am actually using devel release to try to learn to fix such problems myself. I will try to help as best as I can though.

---

### Post by hacc on 2010-02-25
xorg.conf
xorg.conf.failsafe
xorg.conf.save
xorg.conf

this is what it showed after I typed that in.

I will have to go to bed soon, I work tomorrow but I can still read these forums. So if I dont reply tonight I will resume tomorrow.

thanks
hacc

---

### Post by NightwishFan on 2010-02-25
Make sure you type any commands case sensitive and correct. My advice is to make sure your xorg.conf is backed up for sure, and then delete the normal one. This sound work. Make sure you type it correctly to the letter, be careful.
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original && rm /etc/X11/xorg.conf
```

To restore backup:
```
cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```

---

### Post by hacc on 2010-02-25
Ok, thanks for your help. Im not sure what was going wrong but it worked this time. Now I just need help installing my intel gma 950 driver, because I dont think it is working properly.

 My goal is to get some kind of game working through wine and the 2 that I have tried so far dont start up. They just dont do anything after the splash screens.

thanks
Andy

---

### Post by NightwishFan on 2010-02-25
Perhaps try a new thread in the Wine forum.

---

