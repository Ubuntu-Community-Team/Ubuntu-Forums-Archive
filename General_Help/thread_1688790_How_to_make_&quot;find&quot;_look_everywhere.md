---
title: "How to make &quot;find&quot; look everywhere?"
date: 2011-02-15
forum: General Help
---

### Post by Mariane on 2011-02-15
I installed seamonkey by typing 

```

sudo apt-get install seamonkey

```

And I did nothing appart from right-clicking on its icon in the menu and choosing "Add to panel". 

Here is my seamonkey.desktop file: 

[Desktop Entry]
Name=Seamonkey
GenericName=Internet Suite
Exec=seamonkey %u
Terminal=false
Type=Application
Categories=GTK;Network;
Icon=seamonkey.xpm

But:

```

cd /
sudo find ./ -name seamonkey.xpm

```

Finds nothing at all. What am I doing wrong? 

Mariane

---

### Post by YesWeCan on 2011-02-15
try
sudo find . -name seamonkey.xpm

or

sudo find / -name seamonkey.xpm

---

### Post by arvevans on 2011-02-15
sudo find /* -name "what_to_find" -print

---

### Post by b0b138 on 2011-02-15
sudo find wheretostart -name word

ex. sudo find / -name seamonkey.xpm

---

### Post by Mariane on 2011-02-15
Thank you all, I tried them: 

sudo find . -name seamonkey.xpm
sudo find / -name seamonkey.xpm
sudo find /* -name "seamonkey.xpm" -print
sudo find / -name seamonkey.xpm

None found it :confused: 

Mariane

---

### Post by arvevans on 2011-02-15
The seamonkey lied.  It is not a .xpm file.

[INDENT]arv@arv-desktop:~$ sudo find /* -name seamonkey.* -print
/usr/share/applications/seamonkey.desktop
/usr/share/app-install/desktop/seamonkey.desktop
/usr/share/pixmaps/seamonkey.png
/usr/lib/seamonkey-2.0.11/chrome/icons/default/seamonkey.png
/var/lib/dpkg/info/seamonkey.md5sums
/var/lib/dpkg/info/seamonkey.list
arv@arv-desktop:~$ 

[/INDENT]

I changed the "xpm" part to a wildcard "*" and it found the icon at /usr/share/pixmaps/seamonkey.png

---

### Post by luigi_mb on 2011-02-16
How about

```

locate seamonkey.xpm

```

Way faster. Here's the output

/usr/share/app-install/icons/seamonkey.xpm


/luigi

---

### Post by Mariane on 2011-02-17
```

locate seamonkey.xpm

```

Doesn't find it either, and nor does:  


```

locate seamonkey.*

```

But

```

sudo find ./ -name seamonkey.*

```

finds the .png icon. Crazy the program could lie about the extension and still function. 

Thanks to you all again! 

Mariane

---

### Post by jim_deadlock on 2011-02-17
```
sudo updatedb
sudo locate seamonkey
```

You don't need to use wildcards with locate, it's already assumed. You should run updatedb first otherwise newer files won't show up.

---

