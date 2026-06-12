---
title: "Browsing windows shares in Thunar"
date: 2011-12-11
forum: General Help
---

### Post by motorcity909 on 2011-12-11
I'm seriously thinking about either Xubuntu or XFCE-on-Ubuntu for my next computer but am still undecided (I know I don't like Unity).

Am I right in saying that Thunar can't browse Windows shares?  Therefore would I have to install Nautilus?  There would be no concerns about bloat and computer power as it's gonna have plenty.

Cheers
Dave

---

### Post by 3Miro on 2011-12-11
I think this is what you need:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Look on the left for the commands to install/uninstall different DE.

---

### Post by Bucky Ball on 2011-12-11
> **motorcity909 said:**
> 

Am I right in saying that Thunar can't browse Windows shares?  Therefore would I have to install Nautilus?  There would be no concerns about bloat and computer power as it's gonna have plenty.

Cheers
Dave

Yes, and yes. Just install Nautilus and set that as the default file manager. I have thunar, nautilus and pcmanfm (which is really fast!) installed on my Xfce box.

And Dingbats, at the login screen, hit 'Sessions' and you will have a choice of Xfce session or regular Ubuntu (Gnome) session. ;)

---

### Post by Toz on 2011-12-11
Thunar _can_ browse windows shares. Just make sure you install gvfs and gvfs-backends.

---

### Post by Bucky Ball on 2011-12-11
> **Toz said:**
> Thunar _can_ browse windows shares. Just make sure you install gvfs and gvfs-backends.

I have both those installed and no network browsing in Thunar for me. How exactly do you do it?

---

### Post by Toz on 2011-12-12
After installing gvfs-backends (and re-logging in), you should get a Network icon in the Thunar sidebar. This will allow you to view to and connect to windows shares.

---

### Post by Bucky Ball on 2011-12-12
Nope, nothing like that here. Backends installed. It has always been a problem with Thunar and no-one has ever suggested (until now) that it was that easy to remedy. ;)

I have Nautilus as my default file manager for this very reason ...

---

### Post by motorcity909 on 2011-12-13
Bucky, have you run into any problems using Nautilus?  I've seen some comments that it takes over the desktop, changes icons and to avoid this has to be run with 'no desktop' in the command?

The other thing Nautilus does that I don't think Thunar does is the ability to open folders in a new tab, hence my interest in using Nautilus instead.

Dave

---

### Post by Bucky Ball on 2011-12-13
No problems here. I'm using 10.10 though and that may make a difference. My regular boot is Ubuntu with Xubuntu-desktop installed and defaulting to Xfce, not Gnome, at the login screen. I have straight Xubuntu installs on other partitions though so I'll try one later. You are using 11.04? Think I have Xubuntu 11.04 installed somewhere!

---

### Post by Bucky Ball on 2011-12-13
I am now typing to you from my Xubuntu 11.04 install and have just installed Nautilus and made it the default file manager and it has changed nothing, nada, zilch, nought. ;)

When opening it from the terminal it made the screen do a bit of a flash but didn't change icons or anything else. Now default it just pops up (I use Windows Key/M (<super>m) as a keyboard shortcut for my file manager).

---

