---
title: "GNOME 3 - installed games dont work"
date: 2011-06-20
forum: General Help
---

### Post by u-noob-tu on 2011-06-20
i recently put GNOME Shell on my laptop (tired of unity and GNOME classic), and discovered that all my games that i had installed wouldnt work. one of my favorites if foobillard. when i click the icon, a message appears that says "no such file or directory, child process failed to start". even after reinstalling, i get the same message for all games that dont come with GNOME 3 (aisle riot solitaire, g brainy, etc.). i know some things changed in file management in gnome 3, is that whats going on?

---

### Post by u-noob-tu on 2011-06-21
*BUMP* im getting a little bored with no games.

---

### Post by dFlyer on 2011-06-21
Have you thought about installing Fedora 15 which comes with native gnome3. That may solve some of your game problems. Gnome3 is currently not native in ubuntu except in very alpha 11.10.

---

### Post by u-noob-tu on 2011-06-21
yes, but i am still somewhat new to linux and ive heard fedora is a more difficult distro to get used to. im quite happy with ubuntu and i dont feel like swapping distros at this point.

---

### Post by dFlyer on 2011-06-21
Fedora is a straight forward install just like ubuntu. The only problem most people have are installing propriety drivers. You might want to download there live cd and give it a try to see if all you hardware works. The only other thing I can suggest at this time is wait for 11.10 to be released or try to find a gnome3 forum.

---

### Post by nothingspecial on 2011-06-22
The problem (I had a while ago) could be that /usr/games is not in your $PATH

Open a terminal and type

```
nano .bashrc
```

Put this at the end of that file

```
export PATH=$PATH:/usr/games
```

Press Ctrl-O, Enter, Ctrl-X

Then type ```
. ~/.bashrc
```

And try a game again.

I appologise if this has got nothing to do with it.

---

### Post by u-noob-tu on 2011-06-22
i found this thread last night: [http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343) it briefly mentions a fix for games not launching at the top of the thread. it worked like a charm. :guitar:

---

