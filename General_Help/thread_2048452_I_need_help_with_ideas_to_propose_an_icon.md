---
title: "I need help with ideas to propose an icon"
date: 2012-08-26
forum: General Help
---

### Post by funenga on 2012-08-26
Hello
I'm using an open-source application called cmus [1] and I like it a lot. I also like Ubuntu and I've made the suggestion (in their mailing list [2]) to create an icon in order to properly integrate cmus with a unity's launcher.
One icon already exists (made by a user from slackware, see [3]) but I think something better could be made.

[LIST]
[*]Does anyone have an idea who can be contacted to create a free icon for the app?
[*]Btw, is there any webpage explaining the process of creating a well behaved unity's launcher?
[/LIST]
More info about cmus can be found in the wikipedia's page of cmus [4] or their webpage [1].

Filipe Funenga
Lisbon PT

[1] [http://cmus.sourceforge.net/](http://cmus.sourceforge.net/)
[2] [http://sourceforge.net/mailarchive/forum.php?thread_name=20120823212210.GA22539%40molb.org&forum_name=cmus-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20120823212210.GA22539%40molb.org&forum_name=cmus-devel)
[3] [http://slackware.org.uk/salix/x86_64/13.1/source/ap/cmus/cmus.png](http://slackware.org.uk/salix/x86_64/13.1/source/ap/cmus/cmus.png)
[4] [http://en.wikipedia.org/wiki/Cmus](http://en.wikipedia.org/wiki/Cmus)

---

### Post by zero2xiii on 2012-08-26
Hay,

My suggestion would be to grab gimp (or inkscape) and start playing. Icons are generally very simple artworks and not a lot of detail go into them.

As for the launcher and all that, I have no idea. Might try some dev pages? Or have a look at [this]("http://itshouldbeuseful.wordpress.com/2011/05/05/create-a-custom-launcher-for-unity-in-ubuntu-11-04/") link.

Cherz

---

### Post by Frogs Hair on 2012-08-26
There appears to be a contact email and forum at the link. [http://gitorious.org/cmus](http://gitorious.org/cmus)

---

### Post by Frogs Hair on 2012-08-26
You can do much better of course , but this took a few minutes on gimp.

---

### Post by funenga on 2012-08-26
:) thank you very much to both

**zero2xiii**: that link helped a lot! I've changed somethings:

1. created a file [FONT="Courier New"]cmus.desktop[/FONT]:
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=/usr/bin/cmus
Name=C* Music Player
Icon=cmus
Keywords=Music;Player;Sound;Playlist

```
2. moved [FONT="Courier New"]cmus.png[/FONT] to [FONT="Courier New"]/usr/share/pixmap/[/FONT]
3. moved [FONT="Courier New"]cmus.desktop[/FONT] to [FONT="Courier New"]/usr/share/applications/[/FONT]
4. Applied the right permissions, owner and group to BOTH files, example:
```

sudo chmod 644 cmus.desktop
sudo chown root:root cmus.desktop

```

**Frogs Hair**: great icon! I'll present your icon to the mailing list and see what they think

---

