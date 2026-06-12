---
title: "add resoulution xorg.conf"
date: 2010-02-12
forum: General Help
---

### Post by wretcher on 2010-02-12
hello my name is will :D 

i have a problem with my xorg.conf i want to add an additional resoulution of 1280 x 1024 . i tried to add it but i failed 2 times i will post my conf. i use ubuntu 9.10 with nautilus gnome


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

i hope you can help me asap. thx

---

### Post by Grenage on 2010-02-12
I have a rough guide [here]("http://www.grenage.com/xorg.html").

---

### Post by wretcher on 2010-02-12
thx Grenage i added new resoulution with a subsection in my conf 
there were no errors when i rebooted but i cant choose this resolution in the nvidia display settings on nautilus hm i will try to solve later but thx for your post i try to fix it and i am sure i will fix it in few months ;P ty see yaa

---

