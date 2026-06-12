---
title: "Question: Downgrade Ubuntu 10.04 to LuBuntu"
date: 2012-01-11
forum: General Help
---

### Post by paulbuk on 2012-01-11
Hi people,
I've had numerous troubles trying to get a relatives 6yr old Acer Aspire 1360 laptop screen to function at 1024 (see thread: [http://ubuntuforums.org/showthread.php?t=1784160](http://ubuntuforums.org/showthread.php?t=1784160)) in order to 'ween' them off winXP.

Now after 6 months of no joy, I think I'll try Lubuntu as it maybe be more co-operative. My question/s is:

- Do I need to completely un-install the Ubuntu 10.40 on the above (probably obvious, yes).

- Would Lubuntu favour an shared integrated SIS VGA (512meg RAM) over Ubuntu's Unity/ Classic or would the same screen issues arise? (leaves a 2 inch black block on the right handside of the screen.

Any directional help/advice much appeciated.

PB

PS - as a user, I'm on 11.04 and 11.10 (-:

---

### Post by raja.genupula on 2012-01-11
hi man just do this to get Lubuntu

sudo apt-get install lubuntu-desktop

after installing that look at that link to get pure Lubuntu

[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

all the best man

---

### Post by paulbuk on 2012-01-11
Hi dude,
That's helpful, I already have the latest Lubuntu (and alt versions) now on CD, so do you advise the sudo's as per your site?
Cheers

PB

---

### Post by Rodney9 on 2012-01-11
sudo apt-get install lubuntu-desktop
will add Lubuntu to your existing Ubuntu, you will be able to select Lubuntu or Ubuntu when you log in.

If you just want just Lubuntu , a clean install maybe what your after.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by underquark on 2012-01-11
Is the laptop able to boot from USB or CD? If it does then I suggest that you try a number of different live CD's/USBs to see which one works best.  I've had success with Puppy Linux on several devices and have managed to get it looking good using the standard VESA drivers if the graphics chip isn't fully supported - you lose some of the special features of the chip but you still get a good GUI and text display.

---

### Post by paulbuk on 2012-01-12
Cheers guys for all your replies.
I managed to get LuBuntu to install fine (automatically removed the previous Ubuntu 11.04). However the screen issue is still there and I'm curious if anyone has answers to what maybe causing the screen problem and how I can fix it fast (see attached screenshot). The screen should be 1024*768, but the VGA output outs a 2inch black margin on the righthand side of the screen, in effect reducing the viewing area (which is a pain!).

The laptop is an Acer Aspire 1360, (PC2700/333mHz), 512RAM (shared graphics). The laptop was bought new with winXP, though I wish to ween my sister off M$ in favour of an Ubuntu strain.

Ubuntu was working great, apart from the screen issue which also effects the current LuBuntu install as listed here in my original post.

Given the choice, I'd rather go back and put Ubuntu 11.04 back on the unit.
Thanks for any advice.
PB
:)

---

### Post by Rex Bouwense on 2012-01-12
That looks like a hardware issue.  I am not familiar with Acer laptops.  Can you adjust the screen?

---

### Post by paulbuk on 2012-01-12
> **Rex Bouwense said:**
> That looks like a hardware issue.  I am not familiar with Acer laptops.  Can you adjust the screen?

I did reduce it last time to a lower res, but the laptop is over at my sisters house on the other side of town, I'm over there again in 2 days, I'll take a look again and adjust to a lower resolution.

(Note, this issue has been going on/off since summer 2010!). Then the new baby arrived. LOL.

PB

---

