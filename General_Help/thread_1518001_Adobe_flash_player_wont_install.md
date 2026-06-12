---
title: "Adobe flash player wont install"
date: 2010-06-25
forum: General Help
---

### Post by al7bar on 2010-06-25
I'm trying to install flash player on my 64 bit xubuntu 9.10

When I run the .deb I get a error

Error: Wrong architecture 'i386'

When I put the .so in the .mozzila/plugins     it doesnt show up... Like it wont import or something.

---

### Post by hansdown on 2010-06-25
Hi al7bar.

That .deb package is for 32 bit.

Look in synaptic package manager, and install

```
flashplugin-installer
```

It will remove conflicting plugins, and install the correct one.

---

### Post by al7bar on 2010-06-25
There was no

```
flashplugin-installer
```


In synaptic package manger 

Help more?

---

### Post by Linuxforall on 2010-06-25
> **al7bar said:**
> There was no

```
flashplugin-installer
```


In synaptic package manger 

Help more?

Please enable partner repository in Lucid, its in synaptic>repositories>other section 

reload and you will have adobe installer.

---

### Post by al7bar on 2010-06-25
ok I installed the installer but still nothing, youtube videos still wont load ;/. 


Any more help??

---

### Post by Oolongtea on 2010-06-25
you need to download a deb file based on your architecture. Look on the adobe website for flash. Then before you download look for your architecture.

---

### Post by al7bar on 2010-06-25
Theres only one .deb

And I tried all others like the .so

Mozzila just wont pick it up.

---

### Post by Oolongtea on 2010-06-25
Try this website:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html]("http://www.cyberciti.biz/tips/linux-install-flash-player-10.html")

---

### Post by al7bar on 2010-06-25
I tried that already...

It wont show up in about:plugins

Ah~!

---

### Post by Oolongtea on 2010-06-25
Perhaps you might get flash if you go to the Ubuntu Software Center and install the Flash Plugin your problems will be solved. I'll keep looking for a solution but that might work.

---

### Post by dcstar on 2010-06-26
[http://ubuntuforums.org/showthread.php?t=1512597](http://ubuntuforums.org/showthread.php?t=1512597)

---

### Post by al7bar on 2010-06-26
Well, I got it to work with that, but now when I click youtube videos there's just a white screen. Help on that?

---

### Post by Oolongtea on 2010-06-26
If you have done what dcstar and I have asked that might be your problem. You might want to uninstall the flash plugin I told you to install due to conflictions it may be having with dcstar's method.

---

