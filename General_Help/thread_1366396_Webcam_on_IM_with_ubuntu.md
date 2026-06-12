---
title: "Webcam on IM with ubuntu"
date: 2009-12-28
forum: General Help
---

### Post by cdneve on 2009-12-28
Hi,

I'm on ubuntu, and I recently got a webcam and tried to use it with emesene and with empathy, but somehow it doesn't work, I can't figure why.
On emesene, when I click on the button that should show me the webcam, an errors occurs, saying : "You don't have libmimic, so you can't send or receive webcam" and so it doesn't work.
On empathy, I simply can't find the button I'm supposed to click on in order to see the webcam ...

All help will be greatly appreciated :)

Thanks ;)

---

### Post by ukaoha ugo on 2009-12-28
have you tried using kopete? check synaptics if you intreseted....

---

### Post by cdneve on 2009-12-28
Yes, I tried Kopete, but I don't know how it works, I don't even know if I'm connected...

---

### Post by Fire_Chief on 2009-12-28
Can you verify that the webcam is working properly on its own?
Easy app for testing is Cheese```
sudo apt-get install cheese
```

Cheers!

---

### Post by cdneve on 2009-12-28
Yes, I installed Cheese, and the webcam works perfectly with it...

---

### Post by cdneve on 2010-01-02
Doesn't anyone know ? :'(

---

### Post by Fire_Chief on 2010-01-04
This should work with Emesene on 9.10 (Karmic) out of the box. If not, then you should try installing python-libmimic & python-dev.
If you are running an earlier version of Ubuntu then this will probably not work for you.

Cheers!

EDIT: Just found this info regarding Empathy in 9.10
[I]**I am using Ubuntu Karmic (9.10) and I can't make MSN call.**

Ubuntu disabled audio/video support in telepathy-butterfly (the MSN backend) because this new feature got introduced too late and that feature didn't get much testing.

You can get more up to date packages from our telepathy ppa, they have audio/video enabled for MSN: [https://launchpad.net/~telepathy/+archive/ppa/](https://launchpad.net/~telepathy/+archive/ppa/)[/I]

---

### Post by cdneve on 2010-01-09
oh, so that explains it I guess.
Will it be introduced later on ?

---

### Post by Fire_Chief on 2010-01-09
It has already been introduced but just wasn't included in Karmic. You can install the package from the PPA (which is newer) and have the functionality now.

Cheers!

---

### Post by n@n@ on 2010-01-14
alo cdneve, i am sooo new to this, but here is what i found:

i have karmik koala, and i'm using emesene to contact friends, like you having problems with the cam. i got the same exact message.
i read somewhere that perhaps downloading python-libmimic would help
so i did.
but i kept getting the same message.
i checked on synaptic package manager, and indeed i had libmimic installed, i actually had the latest version. but i was still getting the same message on emesene.
soooo, i went to emesene and under options, submenu preferences, i found a tab that says "webcam." with my cam connected to my computer i chose the webcam i wanted "to use for my conferences" and right a way i saw my image in the little window under such tab.
have you tried that? 
i hope it helps.

---

### Post by cdneve on 2010-01-15
thanks a lot that should do :P

---

### Post by cdneve on 2010-01-16
I found the part that talks about the webcam, and I can see my picture under it, but apparently my contacts can't see me, is it normal ?

---

