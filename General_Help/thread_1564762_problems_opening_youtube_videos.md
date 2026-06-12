---
title: "problems opening youtube videos"
date: 2010-08-31
forum: General Help
---

### Post by linux810 on 2010-08-31
[SIZE=2]After I upgraded from ubuntu 8.04 to 8.10 I have had problems viewing all videos on youtube etc.

 I have installed the latest flashplayer 10 and gnash and vlc[/SIZE],[SIZE=2] mplayer etc. but still have no luck[/SIZE].

[SIZE=2]Can anyone help with how to solve this problem?
thank you





[/SIZE]

---

### Post by varunendra on 2010-09-01
Have you installed flashplugin-installer?

Close the browser, open synaptic, type flash in the search box. In the showed up list, uninstall all the previously installed flash plugins, and reinstall only **flashplugin-installer** from adobe.

In case it doesn't give satisfactory performance, try flashplugin-nonfree then. But remember- one plugin at a time! Uninstall existing before installing another one.

And by the way, it always helps if you provide your hardware details while posting a problem.

---

### Post by t0p on 2010-09-01
Is there any particular reason why you've installed flashplayer 10 *and* gnash?  Just one will do (I recommend you remove gnash:

```
sudo apt-get remove gnash
```

and just install flashplugin-nonfree:

```
sudo apt-get install flashplugin-nonfree
```

Works for me just fine.)

---

### Post by linux810 on 2010-09-14
Thank you for your advice.
 
I tried what you said, but I am still having problems with viewing videos.
 
I still get a black screen with the circle in the middle moving around but no picture or sound.
 
I am also having another issue, I tried to save a document to my home folder and got an error message stating that I had no disk space, this is the first time I have received this.
 
I tried deleting some programs throught synaptic package manager that I don't use, such as Pidgin, evolution, bluetooth, but still not luck.
 
Thank you for your time
 
linux810

---

