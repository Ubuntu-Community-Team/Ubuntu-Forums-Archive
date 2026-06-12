---
title: "good remote desktop program"
date: 2010-07-30
forum: General Help
---

### Post by philipballew on 2010-07-30
hi. i am looking for reomte desktop software that will allow me to not only view this particular desktop from miles away but send files back and fourth between the two computers. any ideas?

---

### Post by LowSky on 2010-07-30
teamviewer... its free

also works on every major OS, even between them.

---

### Post by davidmohammed on 2010-07-30
teamviewer is nice - but costs if you are running a business

X2go is opensource and you can share folders between computers to copy files back and forth.  As a bonus - you can hear the remote PC audio.

---

### Post by HermanAB on 2010-07-30
SSH of course.

Most of my servers are in the USA and I am currently in the UAE which is approximately on the other side of the globe.  So provided that you are on the same panet, SSH works fine.

---

### Post by Raymond2201 on 2010-07-30
Remote desktop is built into Ubuntu by default but is disabled: System> Preferences > Remote Desktop.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

This system is VNC, which is fine for accessing your PC in your local network but a bad idea if your wanting to use it over the internet as your passwords and all the transmission is unencrypted by default.

I would personally suggest using a ssh server that will encrypt all transmissions over the internet, however by default this will only give you command line access to your system.
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/openssh-server.html)

you can combine these two technologies so vnc runs over your ssh connection, thus it is secure.
here is a nice guide 
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

explains a little about vnc>ssh


hope this helps.

---

### Post by philipballew on 2010-07-30
how can i have ssh and still have a gui. sorry i have only been using linux for 3 years so still not amazing at it yet?

---

### Post by davidmohammed on 2010-07-30
the last posts last link gives you all the info you need if you want to use the inbuilt VNC viewer.  

FreeNX, x2go or teamviewer wrap up their software with ssh so that you dont have to worry about the complexities...

---

### Post by philipballew on 2010-07-30
so these software make this whole process simple  basicly?

---

### Post by alexandari on 2010-07-30
> **philipballew said:**
> so these software make this whole process simple  basicly?


Yea most of them. I also recommend teamviewer

---

### Post by Raymond2201 on 2010-07-30
> **alexandari said:**
> I also recommend teamviewer

Seems like a nice program :)

wish i knew about it 2 + years ago tho hehe

---

### Post by philipballew on 2010-07-31
now with team viewer can i get at the other computer if no one is at it?

---

### Post by Raymond2201 on 2010-07-31
If you look in the options>security you can set up a password for unattended access.

I have been having a play around with this teamviewer software the last day or so and it seems good generally, it seems limited to a more support software package in my view. for e.g. helping friends or family out with their computer problems and such like.

For some reason teamviewer is also using the teamveiwer servers to bounce the connection around it would seem, this is uneeded really and what happens if they go out of buisness? you wont be able to use the software assuming the connections to their servers are critical to the operation of the application.

I think i will stick to SSH as all of what i need to do (and more!) can be done with the CLI or using a gui program like filezilla or something for copying files from your PC.

---

