---
title: "Unable to set default browser"
date: 2012-08-27
forum: General Help
---

### Post by dyerseve726 on 2012-08-27
I have been unable to set any browser other than Firefox as my default in Xubuntu 12.04.  I'm getting this error ```
Aug 27 03:10:24 noah-Divvy001 kernel: [ 2927.033432] exo-helper-1[9284]: segfault at 0 ip 00007fc3772e7a70 sp 00007fffe93cc4f0 error 4 in libxfce4util.so.6.0.0[7fc3772e0000+d000]
```

I reinstalled everything that matched libxfce4util in synaptic, to no avail.  I've tried setting it as default via gui, terminal, from within Chrome (which thinks it's set as default), and by simply uninstalling firefox.  Apps still default to Firefox or, if I've uninstalled it, ask me what to do. 

via settings-->preferred applications   I'm able to see and choose Chrome, but the window quickly reverts back to the previous menu and going back into preferred applications shows that firefox is still chosen.  

I'm at my wits end with this one.  Any help would be very appreciated.

---

### Post by neur0 on 2012-08-27
Have you tried:
```
sudo update-alternatives --config x-www-browser
```

---

### Post by dyerseve726 on 2012-08-27
Yep,  that was the first thing I tried. It tells that chrome is my default. It makes no difference in real use.

---

### Post by neur0 on 2012-08-27
Which browser opens when you type:
```
exo-open --launch WebBrowser
```

---

### Post by Toz on 2012-08-27
Hello @dyerseve726 and welcome to the forums.

Here is something that I've noticed:
> **dyerseve726 said:**
> I have been unable to set any browser other than Firefox as my default in Xubuntu 12.04.  I'm getting this error ```
.....error 4 in [COLOR="Red"]libxfce4util.so.6.0.0[/COLOR][7fc3772e0000+d000]
```

libxfce4util.so.6.0.0 is a part of Xfce 4.10. Xubuntu 12.04 comes with libxfce4util.so.4.1.1 ( Xfce 4.8 ). Did you install Xfce 4.10? If so, how (PPA, build from source)?

What does the following command return?
```
ls -l /usr/lib/libxfce4util.so*
```

Perhaps you have a library mix-up.

---

### Post by CrusaderAD on 2012-08-27
[This]("http://ubuntuforums.org/showthread.php?t=775613") thread has a few ideas.

---

