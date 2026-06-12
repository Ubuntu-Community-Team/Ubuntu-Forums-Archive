---
title: "Recently upgraded from 9.04 to 10.04 and hited the wall."
date: 2010-05-25
forum: General Help
---

### Post by WutCake on 2010-05-25
i've recently decided to upgrade to 10.10 from my 9.04 ubuntu macine, i first updated to 9.10 using the upgrade manager, then to 10.04, now i cant boot into ubuntu, the screen says something about error 273 statues 5, but however, it goes to low-graphic mode and tells me that theres no driver what so ever, so i cant hit that "okey" button.

i don't know how to explain it, and it would be hard to type it all down to tell you guys the errors, but i've catched 273 and statues 5, and something with unreadhead or whatever it said.

i do not wish to do a clean install and i have a live cd from the Jaunty version (9.04).

thank you; hope you can help me :(

---

### Post by Hastor on 2010-05-25
What type of accessability do you have to your files? I know you said you went into low-graphic mode, but does that mean yohu can't boot, period, or that you just can't interact once you boot? Also, could you supply some description of your hardware? That might be a factor in this and is generally helpful to hose that know a lot more about these things (not me).

---

### Post by dino99 on 2010-05-25
grub2 cant work if grub1 and menu.lst have not been removed. Only grub-pc and grub-common have to be installed, then:

sudo grub-mkconfig
sudo update-grub

for your video driver issue, you need to tell us which card/chipset you use

but you can first remove xorg.conf, as its no more needed

sudo rm -f /etc/X11/xorg.conf

---

### Post by WutCake on 2010-05-25
> **Hastor said:**
> What type of accessability do you have to your files? I know you said you went into low-graphic mode, but does that mean yohu can't boot, period, or that you just can't interact once you boot? Also, could you supply some description of your hardware? That might be a factor in this and is generally helpful to hose that know a lot more about these things (not me).
i can't boot, the "warning" that i went low-graphic mode is just sitting there, i cant click ok, the keyboard and mouse isnt working.

also, i dont want to be mean, but it would help if you could spell correctly and use space better :( minor problem btw.

my hardware is no problem really, it should work since it worked fine before, no? anyhow, im using Nvidia graphiccard.

> **dino99 said:**
> grub2 cant work if grub1 and menu.lst have not been removed. Only grub-pc and grub-common have to be installed, then:

sudo grub-mkconfig
sudo update-grub

for your video driver issue, you need to tell us which card/chipset you use

but you can first remove xorg.conf, as its no more needed

sudo rm -f /etc/X11/xorg.conf

and how am i supposed to do what without booting?

---

### Post by Hastor on 2010-05-26
Do you have a duel-boot or was ubuntu your only operating system?If ubtuntu was your only one then you might have to end up doing a clean install. 

I'm cool with spacing and at the time my spell check was acting wacky. I just got here and don't exactly know the ins and outs of this forum yet in concern to post standards. 

The only thing I could vaguely think of that might end up working if Ubuntu was your only boot-able OS would be some form of remote desktop. The only problem is that if you can't access your computer then you just have to cross your fingers that you have remote desktop already enabled. 

Honestly, I think you might just have to abandon ship on the files you have in ubuntu. Good luck, man.

---

### Post by WutCake on 2010-05-26
> **Hastor said:**
> Do you have a duel-boot or was ubuntu your only operating system? If ubuntu was your only one then you might have to end up doing a clean install.

better up, i got triple-boot!
(windows thu.)

> I'm cool with spacing and at the time my spell check was acting wacky. I just got here and don't exactly know the ins and outs of this forum yet in concern to post standards. 

i don't know what in and outs on this forum either but i keep my threads where they are most likely to be.

> The only thing I could vaguely think of that might end up working if Ubuntu was your only boot-able OS would be some form of remote desktop. The only problem is that if you can't access your computer then you just have to cross your fingers that you have remote desktop already enabled.

ohnoes, good thing that i got more OS:s!

> Honestly, I think you might just have to abandon ship on the files you have in ubuntu. Good luck, man.

AyAy Captain! [COLOR="White"]noway man.[/COLOR]

---

### Post by WutCake on 2010-05-28
Okey, status report,

i booted into livecd and removed the xorg.conf as suggested in other threads, i was able to boot into the OS without "Low Graphic Mode", but however, no mouse or keyboard support (not even the light on Caps is reacting xD).

suggestions?

---

### Post by WutCake on 2010-05-29
_[SIZE=1][SIZE=4][COLOR=DarkOrange]B[/COLOR][/SIZE][SIZE=3][COLOR=Indigo]u[/COLOR][/SIZE]**[SIZE=2][COLOR=DeepSkyBlue]m[/COLOR][/SIZE][SIZE=1][COLOR=Lime]p[/COLOR][/SIZE]**[/SIZE]_ :guitar:

---

### Post by WutCake on 2010-05-31
_[SIZE=1][SIZE=4][COLOR=DarkOrange]B[/COLOR][/SIZE][SIZE=3][COLOR=Indigo]u[/COLOR][/SIZE]**[SIZE=2][COLOR=DeepSkyBlue]m[/COLOR][/SIZE][SIZE=1][COLOR=Lime]p[/COLOR][/SIZE]**[/SIZE]_ :guitar: again :(
cmon guys..

---

### Post by WutCake on 2010-06-03
why no response? :3

---

