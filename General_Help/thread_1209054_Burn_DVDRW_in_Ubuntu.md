---
title: "Burn DVD/RW in Ubuntu"
date: 2009-07-09
forum: General Help
---

### Post by masterton on 2009-07-09
I would like to try to burn data to DVD+RW in Ubuntu LiveCD.
Ubuntu has a simple CD/DVD creator tool installed by default.

1) Is there any more advanced burning software readily available in the repository? (I don't know how to install program which has to be complied first)

2) I don't see it offers an option whether to permanently close a DVD or not when using the simple CD/DVD creator. I'm afraid the burn will close my DVD/RW permanently (rejecting any further burns). Anyway I would like to know how to do both.

How can I burn **without** closing the DVD/RW permanently?
How can I burn **AND also** close the DVD/RW permanently?

Thanks a lot. [IMG]http://www.wilderssecurity.com/images/smilies/biggrin.gif[/IMG]

---

### Post by synapsys on 2009-07-09
Try gnomebaker.

---

### Post by zerhacke on 2009-07-09
I personally like K3b for KDE, and if you install it on X or U buntu you can still use it even if you don't have KDE installed.  The thing is, it doesn't support nonfree media formats out of the box so if you want to burn a music CD you'll need another apt-get to make it work.  Since you said you want a Data CD you don't have this problem.

However... there's no way for you to burn the CD unless you have multiple CD/DVD ROMs.  You can't eject the live CD while it is being used.

---

### Post by masterton on 2009-07-10
> **synapsys said:**
> Try gnomebaker.

How could I use/install?
I couldn't find it in the Add/Remove program dialog.

---

### Post by 6205 on 2009-07-10
What's wrong with 'Brasero Disc Burner'? Ubuntu's default burning app.

You don't need to use CD/DVD Creator..

---

### Post by masterton on 2009-07-10
> **zerhacke said:**
> I personally like K3b for KDE, and if you install it on X or U buntu you can still use it even if you don't have KDE installed.  The thing is, it doesn't support nonfree media formats out of the box so if you want to burn a music CD you'll need another apt-get to make it work.  Since you said you want a Data CD you don't have this problem.

About K3b, where is the option to _permanently close_ or _not close_ the DVD/RW?
I'm afraid it will finalize my disc which I don't tell it to.

> **zerhacke said:**
> However... there's no way for you to burn the CD unless you have multiple CD/DVD ROMs.  You can't eject the live CD while it is being used.
Glad that I have multiple disc drive. ;)

---

### Post by masterton on 2009-07-10
> **6205 said:**
> What's wrong with 'Brasero Disc Burner'? Ubuntu's default burning app.

You don't need to use CD/DVD Creator..

The same question remains. Where is the option to permanently close or not close the DVD/RW?
I'm afraid it will finalize my disc which I don't tell it to.

---

### Post by libra1780 on 2009-07-10
> How could I use/install?
I couldn't find it in the Add/Remove program dialog.
you have to enable univerese repos. you can change it with a prog in the system tag. don't know how it's calles on gnome

latest should be gnomebaker_0.6.4-1_i386

---

### Post by 6205 on 2009-07-10
> **masterton said:**
> The same question remains. Where is the option to permanently close or not close the DVD/RW?
I'm afraid it will finalize my disc which I don't tell it to.

I don't know how abou DVD's but i am 100% sure that when i burn CD i have always option to close disc or leave it open(multisession)


EDIT: OK, looks like it's possible somehow, option for open/close disc is there, but i don't why it's faded out and you cannot check or uncheck it...

---

### Post by masterton on 2009-07-10
Oh I see. Thanks.
But it's weird that the four options are greyed out. See my screenshot:
[img]http://ubuntuforums.org/attachment.php?attachmentid=120563&d=1247225719[/img]

How can I "un-grey" the options?

---

### Post by 6205 on 2009-07-10
Hmm... i don't understand that neither :(

---

### Post by masterton on 2009-07-10
> **zerhacke said:**
> I personally like K3b for KDE, ...  The thing is, it doesn't support nonfree media formats out of the box so if you want to burn a music CD **you'll need another apt-get to make it work**. 

I may need to do this in future so I'd better ask now.
What apt-get do I need if I want to burn a music CD? Thanks. :D

---

### Post by zerhacke on 2009-07-11
sudo apt-get install libk3b2-extracodecs

---

### Post by masterton on 2009-07-12
> **zerhacke said:**
> sudo apt-get install libk3b2-extracodecs
Thanks a lot.

---

