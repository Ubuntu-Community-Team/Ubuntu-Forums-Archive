---
title: "Firefox installer not working! Heeelp!"
date: 2010-04-01
forum: General Help
---

### Post by ShadowsOfSilver on 2010-04-01
Okay, I'm new to Kubuntu - but not Ubuntu. I installed Kubuntu about 2 hours ago, and I'm stuck... When I run the Firefox installer, it says the package is already installed, but where? I'm using Konqueror right now, but I want to use Firefox.

---

### Post by llawwehttam on 2010-04-01
Firefox installer? What installer. If from the mozilla site then it is not an installer as such, just a tar compressed file AFAIK.

Look where you uncompressed it.

If you did Install it right it will be in /usr/bin or /opt/

---

### Post by ShadowsOfSilver on 2010-04-01
No - the installer was already there, I'm using 9.10...

---

### Post by koolblue3 on 2010-04-01
Hi,

Have you tried to install Firefox through the terminal? Here is the command to install Firefox through the terminal.
```

sudo apt-get install firefox

```

---

### Post by Chesamo on 2010-04-01
If it's already installed, all you have to do is
```
firefox
```
in the Terminal.

By "where" I assume you mean where is the shortcut. If you can't find one, you can always just make a Launcher with "firefox" as the command to execute.

Programs are installed into /usr/bin or /opt, but you really don't want to be mucking around in there. Here be dragons!

---

### Post by lovinglinux on 2010-04-01
> **llawwehttam said:**
> Firefox installer? What installer. If from the mozilla site then it is not an installer as such, just a tar compressed file AFAIK.

Look where you uncompressed it.

If you did Install it right it will be in /usr/bin or /opt/

KDE comes with a launcher to install Firefox. Is just a menu item that triggers the installation of Firefox from the repositories. This was introduced with Karmic.

So the OP is talking about the default Firefox installation, not an extracted tar file downloaded from Mozilla.

If the installation didn't create a menu, then add it yourself. 

The default Firefox command is **firefox %u**.

If the installation didn't work, then install Firefox with command-line:

```
sudo apt-get install firefox
```

---

### Post by Pikestaff on 2010-04-01
You can also try UbuntuZilla... I have never had any problems with it.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by mocoloco on 2010-04-01
Did the same thing a month or so ago.  Firefox showed up in the menu after logging out and back in I think.  Not sure why.

---

### Post by ShadowsOfSilver on 2010-04-02
Thanks guys! It said "Selected Pacakges are already installed" before. Used sudo apt-get install firefox like suggested, and it worked! (I would have done it, but I didn't know if the code was the same, I didn't want to ruin my brand new install...) Thanks everyone for your help!

---

