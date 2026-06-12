---
title: "Intalling/Uninstalling application"
date: 2010-10-12
forum: General Help
---

### Post by sfg on 2010-10-12
Hi,

I have two questions.

First: If I download a game (or application) as a tar.gz and then unpack it, how could I get a shortcut to it that also has that application's icon? Basically, I'd like to have something similar to what you get by using Ubuntu Software Center, but not all applications I want are available there or they're not the latest version. Note that the files that launch the programs I'm talking about don't show the icon after I unpack them... just a generic one. 

Second: If I install a deb package, how can I then uninstall all the dependencies that it also installs? I found out how to uninstall the package itself, but the dependencies remain. Is there any way to do that? 

Thank you.

---

### Post by andrewthomas on 2010-10-12
```
sudo apt-get autoremove
```

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by sfg on 2010-10-12
Thank you very much. 

Anyone can help me with the first question too?

---

### Post by emoguitarist06 on 2010-10-12
Right click you applications menu and edit and then add new item to whatever menu you like I guess in this case Games

Then you'll locate the "launcher" probably a .bin file and voila!
Then you can use any premade pics for it or you're a graphical editor type you can use Inkscape to make an svg for the icon

---

### Post by sfg on 2010-10-12
But if those applications have icons when installed from Ubuntu Software Center doesn't it mean they have the icon somewhere in their files? That's basically what I'm trying to find out...

---

### Post by WorMzy on 2010-10-12
Icons are usually installed to system directories like /usr/share/pixmaps/.

---

