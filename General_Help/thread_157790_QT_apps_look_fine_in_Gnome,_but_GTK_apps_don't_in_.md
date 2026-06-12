---
title: "QT apps look fine in Gnome, but GTK apps don't in kde"
date: 2006-04-09
forum: General Help
---

### Post by AdotB on 2006-04-09
Hi, I have Gnome and KDE installed, does anyone know why qt apps look fine in gnome (even the kde icon them is used when using konqueror under gnome), but gtk apps dont apply a theme in kde?

Thanks

---

### Post by adamkane on 2006-04-09
How to make QT apps look more Gnome-ish or KDE-ish:
[http://ubuntuforums.org/showthread.php?t=76633](http://ubuntuforums.org/showthread.php?t=76633)

---

### Post by AdotB on 2006-04-09
[QUOTE=adamkane]How to make QT apps look more Gnome-ish or KDE-ish:
[http://ubuntuforums.org/showthread.php?t=76633](http://ubuntuforums.org/showthread.php?t=76633)[/QUOTE]

Thanks, but i was wondering why gtk apps wont aply themes in kde the way qt apps do in gnome. (sorry if i wasn't clear, and thanks for the link)

---

### Post by adamkane on 2006-04-09
Looks like the trick is to make GTK use the QT engine:
[http://www.freedesktop.org/wiki/Software_2fgtk_2dqt](http://www.freedesktop.org/wiki/Software_2fgtk_2dqt)

Report how well it works. There isn't a lot of information yet about using this engine in Ubuntu.

---

### Post by AdotB on 2006-04-10
Hmm...
 
 I tried compiling GTK-Qt from source, but it sais I don't have kde headers installed ?? So i tried their repository to my source.lst but that didnt work either.

I'm afraid im not savy enough to figure that header thing out.

---

### Post by adamkane on 2006-04-10
Would you be willing to post the error message you received?

If the error is long, you can post the message using the quote tag. I inserted spaces, so that you can see how it is done.

[ quote]
Error message line 1
Error message line 2
[ /quote]

---

### Post by AdotB on 2006-04-10
Sure, while doing ./configure this messege eventually stops it: 
> checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

Also, I just found gtk2-engines-gtk-qt in synaptic and it provides a way to configure it in kcontrol, although it does not seem to be working.

-- Edit --
gtk2-engines-gtk-qt, installed from synaptic does workwith some gtk apps, but the gnome icons are still there and it does not seem to work with root apps (such as synaptic).

---

### Post by adamkane on 2006-04-10
You may need to run kcontrol as root to make changes.

If that doesn't work, you can try this to make your GTK themes work as root:

```

sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts

```

---

### Post by AdotB on 2006-04-10
> You may need to run kcontrol as root to make changes. Running KDE apps as root causes permission problem with various files that make KDE unusable.

And I've already linked my themes to the /root/ folder and that doesn't help because GTK doesn't work in kde for some reason (which was the origional problem).  But everything except Synaptic  looks fine now so i'm happy. Thanks for your help.

---

### Post by AdotB on 2006-04-11
Hey, I just wanted to say i did some more searching and found a thread with the answer to the root program problem:

[http://ubuntuforums.org/showthread.php?t=113324](http://ubuntuforums.org/showthread.php?t=113324)

Synaptic look just fine now.

---

### Post by adamkane on 2006-04-21
Cool. Thanks. I'll add it to my Ubuntu-Look bookmarks.

---

