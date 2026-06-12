---
title: "Background"
date: 2006-05-27
forum: General Help
---

### Post by Ruben123 on 2006-05-27
Hej, i tink this is allready posted. but i can't find :s

i saw on a screen shot a dektop where the background whas filled up with wheathet details, cpu % , and some other things, do somboddy know where i also can find those things?

thanks

---

### Post by aysiu on 2006-05-27
Superkaramba is your friend.

It's in the Universe repository: ```
Package superkaramba

    * warty (kde): A program based on karamba improving the eyecandy of KDE [universe]
      0.33-5: amd64 i386
    * hoary (kde): A program based on karamba improving the eyecandy of KDE [universe]
      0.35-2ubuntu2: amd64 i386 powerpc
    * breezy (kde): A program based on karamba improving the eyecandy of KDE [universe]
      0.36-1ubuntu2: amd64 i386 powerpc
    * dapper (kde): a program based on karamba improving the eyecandy of KDE [universe]
      4:3.5.2-0ubuntu8: amd64 i386 powerpc
``` If you have no idea what I just said, read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by johnc4510 on 2006-05-27
install this: gdesklets
Use the synaptic package mgr.
System>Administration>Synaptic Package Manager

---

### Post by aysiu on 2006-05-27
[QUOTE=johnc4510]install this: gdesklets
Use the synaptic package mgr.
System>Administration>Synaptic Package Manager[/QUOTE] Yes, if you happen to be using Gnome but accidentally posting in the Kubuntu section, you would use gDesklets instead of Superkaramba.

---

### Post by asimon on 2006-05-27
[QUOTE=johnc4510]install this: gdesklets
Use the synaptic package mgr.
System>Administration>Synaptic Package Manager[/QUOTE]
gdesklet is for Gnome what superkaramba is for KDE. I think because this is the KDE subforum, superkaramba is more appropriate then gdesklets. ;-)

---

### Post by johnc4510 on 2006-05-27
Sorry, didn't read the header

---

### Post by Ruben123 on 2006-05-27
ok, i am a linux noob :p

I just downloaded the superkaramba, i coudn't find it in my paketmanager. 

but how do you install int, its a tar.gz file, i unpacked it, but what i need to do after that ??

---

### Post by aysiu on 2006-05-27
It's in the repositories--you just have to enable extra ones.

Please read this link. You won't regret it.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ruben123 on 2006-05-27
it seems to hard for mee :s

when i do this
sudo ./configure --prefix=/opt/kde3/make install

i get this

configure: WARNING: you should use --build, --host, --target
checking build system type... Invalid configuration `install': machine `install' not recognized
configure: error: /bin/sh admin/config.sub install failed

---

### Post by aysiu on 2006-05-27
[quote=Ruben123]it seems to hard for mee :s[/quote] Don't compile from source. Install from the repositories.

First, delete the .tar.gz you downloaded and the folder you extracted from the .tar.gz

Second, follow these steps to get the extra repositories you need for Superkaramba: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Third, paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install superkaramba
```

Finally, read this link so you know how to install software the *easy* way: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Ruben123 on 2006-05-27
is it normall that i see nothing after doing this kdesu kwrite /etc/apt/sources.list 
even not ruben@computer:- $

---

### Post by aysiu on 2006-05-27
[QUOTE=Ruben123]is it normall that i see nothing after doing this kdesu kwrite /etc/apt/sources.list 
even not ruben@computer:- $[/QUOTE] So it looks like this? ```
ruben@computer:~$kdesu kwrite /etc/apt/sources.list


``` or it looks like this? ```
ruben@computer:~$kdesu kwrite /etc/apt/sources.list
ruben@computer:~$
```

Well, either way is bad if KWrite doesn't actually pop up.

This is what you *should* see (the attached screenshot).

---

### Post by Ruben123 on 2006-05-27
he's bussy whith the update know, i hope this will be ok :s

it was looking like the fist, but with sudo in front of it, it works

---

### Post by Ruben123 on 2006-05-29
It's working ;) i don't have te newest version, but it looks good ;) thank you all

---

