---
title: "&quot;Specified location is not supported&quot; When Dragging and Dropping Files from Browser"
date: 2012-08-12
forum: General Help
---

### Post by Spiralagnus on 2012-08-12
I have a minimal install of Ubuntu and XFCE.  When I try to drag an image from either Firefox or Chrome to the desktop, I receive the error message

```
The specified location is not supported
```

[IMG]http://i48.tinypic.com/1jaz5e.png[/IMG]

Standard behavior in Windows is for the file to be saved to the desktop automatically, and I've heard many users claim that this works in Linux as well.  Right-clicking on the image file -> Save Image As... works fine, but it's not my preferred method of saving images.  Any help would be appreciated. Please let me know if you require more information.

---

### Post by Toz on 2012-08-12
Hmmm, it works here on a clean xubuntu install dragging/dropping from firefox. 

What version of ubuntu are you running and what version of Xfce?

Is xfdesktop running?

---

### Post by Spiralagnus on 2012-08-12
> **Toz said:**
> Hmmm, it works here on a clean xubuntu install dragging/dropping from firefox. 

What version of ubuntu are you running and what version of Xfce?

Is xfdesktop running?

I'm running Ubuntu 12.04 with XFCE 4.8.  xfdesktop is installed and running.  This is a minimal install that I've been building from the ground up, not Xubuntu.  Is there something in Xubuntu to make drag and drop work that might be missing in my installation?

---

### Post by Toz on 2012-08-12
What do the following commands return:
```
env | grep -i xdg
```
```
xprop -root _DT_SAVE_MODE
```
```
ps -ef | grep -i 'xfdesk\|naut' | grep -v grep
```

And just to be sure, do you have icons displayed on the screen?

---

### Post by Spiralagnus on 2012-08-12
> **Toz said:**
> What do the following commands return:
```
env | grep -i xdg
``````
xprop -root _DT_SAVE_MODE
``````
ps -ef | grep -i 'xfdesk\|naut' | grep -v grep
```And just to be sure, do you have icons displayed on the screen?

```
env | grep -i xdg
```returns

```
XDG_MENU_PREFIX=xfce-
XDG_SESSION_COOKIE=be75ae65026c52256d40436200000c15-1344817163.68607-356537508
XDG_CONFIG_DIRS=/etc/xdg/xdg-xfce:/etc/xdg:/etc/xdg
XDG_DATA_DIRS=/usr/share/xfce:/usr/local/share/:/usr/share/:/usr/share
XDG_CURRENT_DESKTOP=XFCE
```and

```
xprop -root _DT_SAVE_MODE
```returns 

```
_DT_SAVE_MODE(STRING) = "xfce4"
```and

```
ps -ef | grep -i 'xfdesk\|naut' | grep -v grep
```returns

```
[my username]    1541  1527  0 20:19 ?        00:00:02 xfdesktop --display :0.0 --sm-client-id 2416d9497-d505-4c17-b67f-8c7a4fc27a48
```My desktop does show icons.  Here's a screenshot of it:

[IMG]http://i47.tinypic.com/34t3dkx.png[/IMG]

Any thoughts?

---

### Post by Toz on 2012-08-12
Hmm. That's similar to my setup. When you try and get that error message, does any extra information show up in the ~/.xsession-errors log file?

I just had a closer look at the screen shot in your first post and noticed that its a thunar error message. Which is interesting. What does the following return?
```
ps -ef | grep thunar | grep -v grep
```

...and what are the contents of your ~/.config/user-dirs.dirs file?

---

### Post by Spiralagnus on 2012-08-13
> **Toz said:**
> Hmm. That's similar to my setup. When you try and get that error message, does any extra information show up in the ~/.xsession-errors log file?

I just had a closer look at the screen shot in your first post and noticed that its a thunar error message. Which is interesting. What does the following return?
```
ps -ef | grep thunar | grep -v grep
```...and what are the contents of your ~/.config/user-dirs.dirs file?

Nothing shows up in ~/.xession-errors when I try to drag and drop an image file onto the desktop.

I am running Thunar, not Nautilus.  Since Thunar comes bundled with xfce, I thought it would be sufficient.  

```
ps -ef | grep thunar | grep -v grep
```

returns nothing.  However,

```
ps -ef | grep thunar 
```

returns 

```
[username]   2400  2315  0 14:10 pts/1    00:00:00 grep --color=auto thunar
```.

The file user-dirs.dirs does not exist in my .config directory.

Any thoughts?

---

### Post by Toz on 2012-08-13
Okay, here's an interesting update. I fired up my Arch Xfce install and sure enough, the drag and drop didn't work. I couldn't find any noticeable differences between the two - except that Xubuntu has some extra configuration settings. Looking through those, I couldn't find anything that made a difference.

On a hunch, I tried a different image on Xubuntu and it _didn't_ work. Apparently only some images work. Here is what I found: if I right-click the image in Firefox and I get a "Save Image As" option, then it copies properly to the desktop. If that option doesn't exit, then it won't copy. I then double checked against my Arch installed and confirmed the same.

Can you try with different images in Firefox and check whether the option to "Save Image As" is required for the action to work?

---

### Post by Spiralagnus on 2012-08-13
> **Toz said:**
> Okay, here's an interesting update. I fired up my Arch Xfce install and sure enough, the drag and drop didn't work. I couldn't find any noticeable differences between the two - except that Xubuntu has some extra configuration settings. Looking through those, I couldn't find anything that made a difference.

On a hunch, I tried a different image on Xubuntu and it _didn't_ work. Apparently only some images work. Here is what I found: if I right-click the image in Firefox and I get a "Save Image As" option, then it copies properly to the desktop. If that option doesn't exit, then it won't copy. I then double checked against my Arch installed and confirmed the same.

Can you try with different images in Firefox and check whether the option to "Save Image As" is required for the action to work?

Hmmm...Every image I try in Firefox, I get the "Save Image As" option.  I can save them all successfully to my local machine, but dragging and dropping them produces the aforementioned error message.  I even tried several different image types.  When drag and drop didn't work for you, did you get this error?  

It seems to me that the problem may lie in how the browser treats save via drag-and-drop differently from save via right-click -> Save Image As..., but I'm not sure what that difference is.  Is save via drag-and-drop a feature of the browser or of the operating system?  Any thoughts?

---

### Post by Toz on 2012-08-13
Wait a second. I just remembered that I'm running an updated version of xfdesktop from another PPA - not the version thats included with 4.8. And on my Arch install, its running the new Xfce 4.10. Maybe that explains why its working for me?

[Here]("http://xfce.org/download/changelogs/4.10pre1") is the first changelog for 4.10 (pre1). Notice there are a couple of drag and drop related fixes.

You could try installing Xfce 4.10 - see: [http://www.techlw.com/2012/05/install-xfce-410-on-ubuntu-or-mint-or.html]("http://www.techlw.com/2012/05/install-xfce-410-on-ubuntu-or-mint-or.html"). You could just run the "sudo apt-get install xfce4" command (like you did last time) if you don't want the whole xubuntu setup.

---

### Post by Spiralagnus on 2012-08-15
> **Toz said:**
> Wait a second. I just remembered that I'm running an updated version of xfdesktop from another PPA - not the version thats included with 4.8. And on my Arch install, its running the new Xfce 4.10. Maybe that explains why its working for me?

[Here]("http://xfce.org/download/changelogs/4.10pre1") is the first changelog for 4.10 (pre1). Notice there are a couple of drag and drop related fixes.

You could try installing Xfce 4.10 - see: [http://www.techlw.com/2012/05/install-xfce-410-on-ubuntu-or-mint-or.html](http://www.techlw.com/2012/05/install-xfce-410-on-ubuntu-or-mint-or.html). You could just run the "sudo apt-get install xfce4" command (like you did last time) if you don't want the whole xubuntu setup.

Well, I upgraded to Xfce 4.10 (thank you for the instructions, by the way, since that was something I was trying to figure out how to do anyway) and ran dist-upgrade, but I'm still getting the same drag-and-drop error message in both Firefox and Chromium.  Any thoughts?

---

### Post by Toz on 2012-08-15
Can you drag and drop a file from Thunar onto the desktop? Does that work?

---

### Post by Spiralagnus on 2012-08-16
> **Toz said:**
> Can you drag and drop a file from Thunar onto the desktop? Does that work?

I can. Drag and drop works extremely well between Thunar and the desktop (although I resent having to hold down Shift to move instead of copy the file).

---

### Post by Toz on 2012-08-16
Any chance you could create a second account on your computer and test the drag and drop there? It would be interesting to see if this is a problem with the system files or the configuration files in your home directory.

---

### Post by Spiralagnus on 2012-08-16
> **Toz said:**
> Any chance you could create a second account on your computer and test the drag and drop there? It would be interesting to see if this is a problem with the system files or the configuration files in your home directory.

I just created a guest account with non-admin privileges.  Drag and drop between Thunar and the desktop work.  Drag and drop between Firefox or Chromium and the desktop still produce the same error.  So I don't think it's a problem with a profile-specific configuration.

---

### Post by Toz on 2012-08-16
Does anything show up in the ~/.xsession-errors log file when the drag and drop fails and you get the error message?

---

### Post by Spiralagnus on 2012-08-17
> **Toz said:**
> Does anything show up in the ~/.xsession-errors log file when the drag and drop fails and you get the error message?

Nope.  I did a tail -f of ~/.xsession-errors, and nothing showed while trying to drag and drop image files to my desktop.  I also looked at the files in /var/log and noticed that none of them had been modified since I first switched on my computer, so the error wasn't going into any of those, either.

---

### Post by Toz on 2012-08-17
Running out of ideas here. Do you have gvfs installed? My system:
```
$ dpkg -l | grep gvfs
ii  gvfs                                   1.12.1-0ubuntu1                         userspace virtual filesystem - GIO module
ii  gvfs-backends                          1.12.1-0ubuntu1                         userspace virtual filesystem - backends
ii  gvfs-bin                               1.12.1-0ubuntu1                         userspace virtual filesystem - binaries
ii  gvfs-common                            1.12.1-0ubuntu1                         userspace virtual filesystem - common data files
ii  gvfs-daemons                           1.12.1-0ubuntu1                         userspace virtual filesystem - servers
ii  gvfs-fuse                              1.12.1-0ubuntu1                         userspace virtual filesystem - fuse server
ii  gvfs-libs                              1.12.1-0ubuntu1                         userspace virtual filesystem - private libraries

```

---

### Post by Spiralagnus on 2012-08-17
> **Toz said:**
> Running out of ideas here. Do you have gvfs installed? My system:
```
$ dpkg -l | grep gvfs
ii  gvfs                                   1.12.1-0ubuntu1                         userspace virtual filesystem - GIO module
ii  gvfs-backends                          1.12.1-0ubuntu1                         userspace virtual filesystem - backends
ii  gvfs-bin                               1.12.1-0ubuntu1                         userspace virtual filesystem - binaries
ii  gvfs-common                            1.12.1-0ubuntu1                         userspace virtual filesystem - common data files
ii  gvfs-daemons                           1.12.1-0ubuntu1                         userspace virtual filesystem - servers
ii  gvfs-fuse                              1.12.1-0ubuntu1                         userspace virtual filesystem - fuse server
ii  gvfs-libs                              1.12.1-0ubuntu1                         userspace virtual filesystem - private libraries

```

Aha!  That did it.  I didn't have gvfs-backends, gvfs-bin or gvfs-fuse installed. I installed them, and now drag and drop works perfectly.  

Thank you very much for all of your help.  Out of curiosity, why are those packages necessary to make drag and drop work?

---

