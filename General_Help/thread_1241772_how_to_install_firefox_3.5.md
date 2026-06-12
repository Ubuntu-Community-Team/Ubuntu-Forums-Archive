---
title: "how to install firefox 3.5"
date: 2009-08-16
forum: General Help
---

### Post by hairchin67 on 2009-08-16
how do i install/upgrade to firefox 3.5. I have downloaded the files already how do i make them go into effect?

---

### Post by djurny on 2009-08-16
for jaunty:

add the ubuntu-mozilla ppa to your apt sources.list
```

cat > /etc/apt/sources.list << EOF
# mozilla firefox ppa
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu jaunty main
EOF

```

update package lists
```

sudo apt-get update

```

import the ppa key
```

KEY=*insert the gpg key apt-get complains about here*
gpg --keyserver subkeys.pgp.net --recv ${KEY}
gpg --export --armor ${KEY} | sudo apt-key add -

```

install firefox-3.5
```

sudo apt-get install firefox-3.5

```

beware that not all stuff works out of the box, i've had some flash issues with shiretoko..

---

### Post by lessgov2007 on 2009-08-16
All I did was install it from the terminal as usual.

Type: sudo apt-get install firefox-3.5

After words there was a shortcut under the "internet" menu. It's a blue orb you can't miss it.

---

### Post by 6205 on 2009-08-16
That is not properly branded Firefox 3.5 and also it does not replace and upgrade Firefox 3.0 to 3.5 like it should, like in for example openSUSE.

With this Shiretoko installed, you will have two web browsers.

---

### Post by oldsoundguy on 2009-08-16
Use Ubuntuzilla.  (available at Source Forge) It works on ALL .deb platforms and builds. Saves all that grief and mucking around every time there is an update .. one visit and one command in terminal and the process becomes GUI after that.

---

### Post by lessgov2007 on 2009-08-16
> **6205 said:**
> That is not properly branded Firefox 3.5 and also it does not replace and upgrade Firefox 3.0 to 3.5 like it should, like in for example openSUSE.

With this Shiretoko installed, you will have two web browsers.

Yes I do have two browsers. I like it that way actually. Good to have a spare. But, like you said it's not rebranded which doesn't bother me. Installing firefox-3.5 from the repos will also install firefox-3.5-branding as well. The only thing you might choose to add is firefox-3.5-gnome-support. I could care less about branding it to firefox. 

But, if you want instructions on doing so there is this thread. [http://ubuntuforums.org/showthread.php?t=1225754](http://ubuntuforums.org/showthread.php?t=1225754)

---

### Post by lovinglinux on 2009-08-17
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

