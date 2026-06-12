---
title: "How to install fonts??"
date: 2009-08-19
forum: General Help
---

### Post by afhkhan on 2009-08-19
[SIZE=3]Greetings to the community!

I am new to Ubuntu and Linux and enjoying it very much. The transition from Windows is gradual but a pleasant one. 

I have around 1000 Fonts that I need to work with. Please help me with the installation of the fonts in the Ubuntu Linux. Help is deeply appreciated.

afhkhan[/SIZE]

---

### Post by credobyte on 2009-08-19
This thread should help you: [http://ubuntuforums.org/showthread.php?t=275202](http://ubuntuforums.org/showthread.php?t=275202)

---

### Post by pmlxuser on 2009-08-19
```

cd ~
mkdir .fonts

```

copy your windows fonts in the ~/.fonts folder 

ctrl + H to show hidden folders in gnome

assuming you have the fonts in a folder say on desktop called FONTS then the command line would be

```

$cd ~/Desktop/FONTS
$ cp *  ~/.fonts

```

log out, log in viola all fonts will appear for you & your application not for your friends.

---

