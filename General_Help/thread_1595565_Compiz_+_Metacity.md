---
title: "Compiz + Metacity"
date: 2010-10-13
forum: General Help
---

### Post by micael3000 on 2010-10-13
Hello.

I've installed Ubuntu 2 days ago, today i was testing some stuff in Compiz and then I decided to reinstall it, my mistake.

I reinstalled compiz, now it doesn't work with metacity anymore.

Whenever i turn on my computer all of the top bars (which contain the close button) disappears! I found some solutions by removing compiz effects (having it "none") but before this problem i was able to get Normal effects on it.

How can I have it back? Make compiz works with metacity?

---

### Post by JOHNNYG713 on 2010-10-13
Be sure window decoration is ticked in your ccsm, or, Try reinstalling libdecoration0 trough synaptic !

---

### Post by Refalm on 2010-10-13
Is the package "compiz-gnome" installed?
Did you turn on "Gnome Compatibility" in CompizConfig?

---

### Post by micael3000 on 2010-10-13
Yes, it is installed... In the CompizConfig it is ON, but still not working when i activate Normal effects...

Now I can turn the system off and on without having bars issues, however, it still doesn't work properly on Normal effects.

---

### Post by micael3000 on 2010-10-13
Window Decoration is on...
The command line there is: "kde4-window-decorator --replace", is it right?

I will try to reinstall however...

---

### Post by micael3000 on 2010-10-13
Reinstalling libdecoration0 fixed my problem!

THANK YOU ALL A LOT!!!!!!!!!!!!!!

Go on, Ubuntu! :)

---

### Post by micael3000 on 2010-10-22
My problem is back...

After i restarted a computer from a NetBeans crash i got all window bars out again.

Can someone PLEASE post a quick-complete-guide using apt-get about how to REMOVE COMPLETELY compiz and then reinstall it, working with metacity?
By reinstalling libdecoration0 I cannot make it work again like last time... I am almost giving up on trying it is really annoying...

Now KDE4-Window-Decorator is crashing everytime I turn my computer on, that's what's making it not work properly...

---

### Post by micael3000 on 2010-10-22
Bump! Help :/

---

### Post by micael3000 on 2010-10-22
I removed Compiz and now i am using no effects...

Hard to make it work so i gave up, theres no guide on Internet who could help me fixing it :/

---

### Post by cottfcfan on 2010-10-22
Are you using Ubuntu or Kubuntu?
You put in your original post "Ubuntu", but why would you want KDE window decorator?
If you are using Kubuntu compiz is always buggy.
If you are using Ubuntu, install fusion-icon, right click and make sure the window decorator is set to GTK.
That should restore your menu bar.


Just an addition, you want to make 'compiz work with metacity'.
Someone will probably correct me but I think you have to use one or the other, not both!

---

### Post by micael3000 on 2010-10-22
I am on Ubuntu, but I didn't install any kde manager, it came right this way.
What shall I do so?
In Fusion icon thats the only option and I am pretty sure that i am using Ubuntu 10.10.

---

### Post by cottfcfan on 2010-10-22
Do you have kde-window-manager installed?
If so i'd uninstall it.
I can't see why that would be there in the 1st place.
For compiz make sure the following packages are installed:

compiz
compiz-core
compiz-plugins
compiz-fusion-plugins-main
fusion-icon
compizconfig-settings-manager
compiz-gnome

If all else fails, i'd try a reinstall, compiz will be used by default.

---

### Post by micael3000 on 2010-10-22
I did it and it worked! :D

Thanks you both, apologies for my newbie approach XD

---

### Post by cottfcfan on 2010-10-22
Glad your sorted.

---

