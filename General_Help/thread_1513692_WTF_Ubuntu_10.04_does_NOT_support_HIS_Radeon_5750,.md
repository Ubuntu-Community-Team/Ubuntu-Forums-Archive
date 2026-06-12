---
title: "WTF??? Ubuntu 10.04 does NOT support HIS Radeon 5750, why? Black screen, HELP!!!!"
date: 2010-06-19
forum: General Help
---

### Post by jekristiansen on 2010-06-19
Hi, i've just tried Ubuntu 10.04 LTS on my computer, but it's just a waste if i can't use it on my 5750 HIS Radeon card, and this is a very common problem wich have been like this ever since it first came out and this is my problem for now.
I'm using it together with a 40 inch Samsung flatscreen, and it should've been possible because it works with Windows 7 flawless.

Anyone here know what i can do to make sure it gonna work with these configurations?
I'm really wanna see for myself how it will look on my 40 inch, so any help with this and i will be very grateful.

---

### Post by Mark Phelps on 2010-06-20
For issues with modern ATI cards, best solution is to visit the Phoronix forums.  They do a LOT of work with moderm ATI cards and have extensive threads dealing with problems and solutions.

---

### Post by jocko on 2010-06-20
> **jekristiansen said:**
> Hi, i've just tried Ubuntu 10.04 LTS on my computer, but it's just a waste if i can't use it on my 5750 HIS Radeon card, and this is a very common problem wich have been like this ever since it first came out and this is my problem for now.
I'm using it together with a 40 inch Samsung flatscreen, and it should've been possible because it works with Windows 7 flawless.

Anyone here know what i can do to make sure it gonna work with these configurations?
I'm really wanna see for myself how it will look on my 40 inch, so any help with this and i will be very grateful.

Exactly what is the problem? What makes you unable to use the card?
Have you installed ati's proprietary drivers yet?

---

### Post by beauboeye on 2010-06-27
I ran into a problem where my 5770 card wouldn't recognize my displays or whatnot during boot-up. A little work around solution I found that **worked for myself**:

[LIST]
[*]Turn off the computer, and take out the card.
[*]Run your computer using your motherboard's built-in video.
[*]Enable your hardware driver -- then install the most recent version of the Catalyst package (for more information about this installation, visit [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide) for more help.)
[*]After your installation is complete, shut-down your computer, throw your card back into your computer, and boot it back up. **(If you happen to have an ASUS motherboard with the Core-unlocking feature, make sure you turn that off before this reboot (you can turn it back on later)... because that had to be done for mine to work.)**
[/LIST]
I hope this will help you :)

---

