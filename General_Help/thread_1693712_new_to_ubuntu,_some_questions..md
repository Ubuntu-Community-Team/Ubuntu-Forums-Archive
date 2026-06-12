---
title: "new to ubuntu, some questions."
date: 2011-02-23
forum: General Help
---

### Post by sogeking99 on 2011-02-23
hey im enjoying linux, i went ahead and gave it a much bigger partition and will only go to windows if i want to play games. but i have a few problems.

first i was wondering if anyone could help me with flash. i got it to install but i cant full screen videos, like ign's and stuff. 

also on windows my asus laptop had some cool features for the touch pad, for example i can tap with two fingers and it counts as as middle mouse button press, three fingers is right click. its very intuitive and means i never have to touch the actual buttons. on ubuntu i can hold down with two fingers to scroll but taping with two is right click. its nitpicking i know but i liked having the middle mouse button as two fingers because i could close tabs easy.

i would also like to learn bash, is there a free book or anything you can recommended? i know most the in's and out's of dos but bash seems pretty interesting.

thanks sorry for long post :D

---

### Post by TeoBigusGeekus on 2011-02-23
Very good [book]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") on bash.

Flash on linux is a sad story, you're not the only one suffering.

Can't help you with the touch pad.

---

### Post by sogeking99 on 2011-02-23
shame flash is a problem, you would think by now there would be better support for it.

thanks for the book

---

### Post by Diametric on 2011-02-23
While not free, I recommend this book:

[http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933](http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933)

It actually goes over stuff to do with the commands and skill you're learning.  Very cool, helpful book.

Cheers.

---

### Post by mastablasta on 2011-02-23
hwo did you install flash? did you install the correct version (eg. 64bit for 64 bit system)?
 
otherwise flash is really not there yet. it depends on too many variables.
 
for example my previous system was fast, sleek only flash was a drag. i changed the GPU, itimporved a bit, still bad. I upgraded the OS, nothing much changed. finnaly i replaced the CPU and now it works nicely.

---

### Post by Spyderkid on 2011-02-23
install ubuntu restricted extras from the software centre

also maybe flash 10 if not included

---

### Post by titsmcgee1230 on 2011-02-23
just install ubuntu-restricted-extras it has flash, java, and everything else you need!

---

### Post by sogeking99 on 2011-02-23
ok cool, how to i install these restricted extras? 64 bit version

---

### Post by trivialpackets on 2011-02-23
From the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by sogeking99 on 2011-02-23
thanks. are there any repository you think i should add?

---

### Post by adrien214 on 2011-02-23
As for the multitouch, you could start [here]("http://lifehacker.com/#!5192139/enable-some-multi+touch-gestures-in-linux").

I didn't look too much in the details because I don't use it myslef, love my mouse too much :P If you search for "multitouch" in the ubuntu forums, you'll see there's plenty of info and questions :P about it)

---

### Post by trivialpackets on 2011-02-23
> **sogeking99 said:**
> thanks. are there any repository you think i should add?

It's entirely up to you I'd say.  If you want to watch DVD's, you may need to install libdvdcss, but that's up to you and "the laws" where you live.  If you're interested in that, you could check out [medibuntu]("http://medibuntu.org/repository.php").

---

### Post by SeijiSensei on 2011-02-23
Actually you don't need to install medibuntu.  After installing ubuntu-restricted-extras, you can run (as root) the script /usr/share/doc/libdvdread4/install-css.sh.  It will download and install libdvdcss2 for you.

---

### Post by sogeking99 on 2011-02-23
cool thanks

---

### Post by sogeking99 on 2011-02-23
i still cant fullscreen most videos and youtube isn't working at all

---

### Post by oldos2er on 2011-02-23
> **sogeking99 said:**
> i still cant fullscreen most videos and youtube isn't working at all

Since you're using 64-bit, get 64-bit flash by clicking the FlashAid link in my sig.

---

### Post by sogeking99 on 2011-02-23
i use chrome, will it effect that or just mozilla?

---

### Post by alphaamanitin on 2011-02-23
> **TeoBigusGeekus said:**
> Very good [book]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") on bash.

Flash on linux is a sad story, you're not the only one suffering.

Can't help you with the touch pad.


AWESOME!  I can put this on my nook now and read a my leisure.

AlphaA

---

### Post by oldos2er on 2011-02-23
> **sogeking99 said:**
> i use chrome, will it effect that or just mozilla?

I believe Chrome comes with its own flash.

---

### Post by sogeking99 on 2011-02-23
ok thanks, i installed it and flash works like a charm now, on mozilla that is. thanks.

found another strange problem, when i go into hibernate (or close laptop) i just seem to get a black screen and cant get it back.

---

