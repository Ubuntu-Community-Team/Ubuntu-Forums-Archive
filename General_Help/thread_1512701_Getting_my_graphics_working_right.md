---
title: "Getting my graphics working right"
date: 2010-06-18
forum: General Help
---

### Post by kaze11 on 2010-06-18
I've a 

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

on my oldish toshiba laptop.

It works sort of, I'm using it now, however everything is very very slow indeed. Very jerky indeed. Scrolling down on firefox takes an age and selecting things is rather hard.
ANy ideas how to get it working right?

---

### Post by clhsharky on 2010-06-18
kaze11

How much memory do you have? And what release are you on?

Sharky

---

### Post by kaze11 on 2010-06-24
10.04 lts

And iirc this laptop has 1gb.


Any ideas about getting this graphics chip working?

---

### Post by kaze11 on 2010-06-25
Anybody? I'm rather clueless on this, all I find searching about is advanced stuff with people trying to figure it having already got it working.
I just need any drivers

---

### Post by kaze11 on 2010-12-31
BUmp?
NEed this laptop now so on the verge of uninstalling ubuntu to try something else (but what...)
This is a really weird problem. SOmetimes when the laptop is turned on everything works fine and normal as a computer should, other times it runs jerky as hell with the screen taking forever to respond to my input.

---

### Post by Grenage on 2010-12-31
Did you install the proprietary ATI drivers?

---

### Post by dino99 on 2010-12-31
on such config, if you want to have something running smootly, you need to forget about heavy apps like firefox or gnome, use lite desktop and app like on netbook: Lubuntu is a good candidate (lxde desktop)

---

### Post by kaze11 on 2010-12-31
> **Grenage said:**
> Did you install the proprietary ATI drivers?

I think i remember doing something like that, IIRC it made things fine for a while but then they went back to normal

---

### Post by Grenage on 2010-12-31
In which case, double check that you are running the proprietary ATI drivers; let's not work on supposition. ;)

---

### Post by kaze11 on 2010-12-31
how do I do that?

---

### Post by Grenage on 2010-12-31
Here's what another has written:

[http://ubuntuforums.org/showpost.php?p=10287270&postcount=8](http://ubuntuforums.org/showpost.php?p=10287270&postcount=8)

The driver might show up under *Administration/Additional drivers*; if so, you can simply enable it there.

---

### Post by kaze11 on 2011-01-02
That thread seems to be a trap
sudo service gdm stop
crashes the computer to a blank screen

---

### Post by clhsharky on 2011-01-02
kaze11


fglrx does not support your legacy chip (ATI Technologies Inc RC410 [Radeon Xpress 200M]) in Ubuntu 10.04.

The open source stack drivers (radeon) is correct, and trying to install ATI proprietary drivers can cause problems.

Check your log file viewer in Xorg.0.log to see if radeon driver is being used, would be a good place to start.
Also turn off visual effects and see if that helps.


Sharky

---

