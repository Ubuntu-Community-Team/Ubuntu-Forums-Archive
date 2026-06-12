---
title: "Can't install gnome-tweak-tool"
date: 2011-11-18
forum: General Help
---

### Post by ripper9100 on 2011-11-18
Hi,

I have 11.10 and tried installing gnome-tweak-tool but i get the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I then try to install gnome-shell and I get the following error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: gnome-icon-theme-full but it is not going to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I then tried to install gnome-session-fallback but I get another dependency error referring to gnome-session-common so I just gave up at that point.

Can someone help me.

---

### Post by fantab on 2011-11-18
Are you using Gnome-Shell or Unity?

If you are using Unity then the problems are explained...  and you don't need gnome-tweak-tool.

---

### Post by ripper9100 on 2011-11-18
I'm using Unity. The reason I'm trying to install gnome-tweak is to change my gtk3.0 theme. I've googled the process of changing the themes for 11.10 and every link I've found points to using this tool but I seem to be the only that is having issues installing it.

---

### Post by cbowman57 on 2011-11-19
Seems I just saw a little tweak app that works well in Unity for such things, if I can just locate the site again.

Haven't used Ubuntu Tweak in quite some time myself but that might do what you want too.

This is where I saw that app, but not certain what all it can do [http://www.omgubuntu.co.uk/2011/11/myunity-is-a-small-simple-unity-tweaking-tool/](http://www.omgubuntu.co.uk/2011/11/myunity-is-a-small-simple-unity-tweaking-tool/)

---

### Post by ripper9100 on 2011-11-19
Thank you for the responses I'll take a look at your link and see if helps me.

---

### Post by guestolo on 2011-11-19
ubuntu tweak might be more what your looking for

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by ripper9100 on 2011-11-19
Yep, Thank You all Ubuntu Tweak did the trick.

---

