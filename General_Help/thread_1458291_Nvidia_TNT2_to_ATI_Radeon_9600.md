---
title: "Nvidia TNT2 to ATI Radeon 9600"
date: 2010-04-19
forum: General Help
---

### Post by Yarbo on 2010-04-19
So I have this old P4, and it had a nVidia TNT2, which is no longer supported under 9.10, so I went and "borrowed" a friend's old 9600, but I can't figure out how to get the drivers to work.

Ubuntu doesn't seem to detect the new card, as it doesn't give me the choice of installing proprietary drivers.

I assume I need to remove all traces of nVidia, and then install something for ATI.

I've also been reading about KMS, which seems interesting, but when I tried to enable it, I got an error.

I want to avoid having to re-install ubuntu if I can.

Please help!

---

### Post by quadproc on 2010-04-19
> **Yarbo said:**
> So I have this old P4, and it had a nVidia TNT2, which is no longer supported under 9.10, so I went and "borrowed" a friend's old 9600, but I can't figure out how to get the drivers to work.

Ubuntu doesn't seem to detect the new card, as it doesn't give me the choice of installing proprietary drivers.
ATI has used the 9600 number in several products so I am not sure which one you have, but it probably doesn't matter.  ATI has dropped support for their legacy cards.  This means that you can't use the current fglrx drivers with any Ubuntu release older than 9.04 if you have a legacy card.  I think that the latest ATI driver that worked with legacy cards was 9.3; that is a problem because that driver is only compatible with the X windows versions which were used before Ubuntu 9.04.

You may be able to get usable results with the open source driver.  Try specifying _Driver "ati"_ in your xorg.conf file.

quadproc

---

### Post by tgalati4 on 2010-04-19
You went from one abandoned card to another.  The open drivers work OK and AMD/ATI seem to be more cooperative with the community, so the open source drivers are improving-albeit slowly.

---

### Post by Yarbo on 2010-04-19
The card I have now, is considerably newer than the one I had.

I did updatedb, then locate xorg.conf and it didn't find anything.,

Any idea what I should do?

---

### Post by clhsharky on 2010-04-19
HI

Your probably on it 'Radeon OSS drivers' it default for your card. 
Whats wrong?

Sharky

---

### Post by Mark Phelps on 2010-04-20
> **Yarbo said:**
> The card I have now, is considerably newer than the one I had.

Doesn't matter -- ATI dropped Linux support for LOTS of cards over a year ago -- including your "newer" one.

The open-source drivers are installed by default, and that's all that is available for your card and recent versions of Ubuntu.

---

### Post by quadproc on 2010-04-20
> **Yarbo said:**
> ...
I did updatedb, then locate xorg.conf and it didn't find anything.,
...

The later versions of Ubuntu do not require an xorg.conf file.  If there is one then it will be used, but if the file doesn't exist then the X server will examine the hardware and try to do what makes sense.  This is probably your situation.

The X server looks in /etc/X11/xorg.conf.

At the present time, I can see three possible approaches to using a legacy card:

1. Downgrade your Ubuntu and fglrx versions to one where support for your card exists;
2. Use the open source driver;
3. Use vesa (really simple but quite robust)

Things may get better in the future because there is a lot of work happening on the open source drivers.  ATI has been good enough to release the software interface specs for their hardware.

quadproc

---

### Post by Yarbo on 2010-04-20
I ended up downgrading to 8.04 for the time being. My 4870 in my main desktop recently crapped out, and I will be unable to replace it for a bit.  So I wanted to be able to use my older machine, and at least able to browse the web and use my screen's native res (2048x1152). On 9.10 is seemed to cap out at 1680x1050, which made everything blurry.

Thanks for the tips everyone!

---

### Post by quadproc on 2010-04-20
> **Yarbo said:**
> ... My 4870 in my main desktop recently crapped out, and I will be unable to replace it for a bit. ...
Do you mind if I ask how long it lasted?  I have two of them and I hope that I didn't choose an unreliable piece of hardware:(

quadproc

---

