---
title: "Lucid Lynx - keyboard not recognised"
date: 2010-06-01
forum: General Help
---

### Post by kolo-01 on 2010-06-01
Hi,
 
I have just updated ubuntu from koala to lynx via reloading the synaptic repositories, and after having restarting, to boot into lynx, found that my laptop's keyboard doesnt work, none of the keys are reponding at all, which is odd as I have never had this problem with my laptop before.. I thought this might have been a (semi) common problem with lynx, but after a few searches, have not found anything similar to this problem.. Does anybody have any idea what might be the problem here, I can still use the laptop to do things via the mouse and even access the internet and grab text and paste it for things, but obviously would like my keyboard back (i didnt write this on my laptop!) I am 99.9% sure it is not a hardware problem
 
any help appreciated

---

### Post by dino99 on 2010-06-01
if you can use mouse or trackball:

tweak : system prefs keyboard, try to select one or an other model

look to .xsession-errors and "system admin log viewer"

which hardware is it ? needed to track the good driver

---

### Post by kolo-01 on 2010-06-01
> **dino99 said:**
> if you can use mouse or trackball:
 
tweak : system prefs keyboard, try to select one or an other model
 
look to .xsession-errors and "system admin log viewer"
 
which hardware is it ? needed to track the good driver
 
 
Thanks for the reply, have tried tweaking the keyboard settings in prefs, but I think the problem is something else.. The laptop is a standard Toshiba, so tried switching the keyboard to that, but it didnt make a difference
 
I am only semi-Ubuntu literate, and looking to the things you say may take a while without a keyboard, so I'll make another post in a bit

---

### Post by dino99 on 2010-06-01
have you checked that the "tosh"* packages are installed into synaptic ?

ie: toshset, toshutils and fnfxd

---

### Post by kolo-01 on 2010-06-01
the keyboard is working again now, i think the problem was something in the repository ppas that shouldnt have been, or something that wasnt there that should.. i changed them about a bit and it seemed to work, but i don think i'll ever know, thanks a lot anyways

---

