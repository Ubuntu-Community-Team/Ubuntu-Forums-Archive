---
title: "Replicate my Ubuntu setup onto another PC?"
date: 2009-08-12
forum: General Help
---

### Post by starbase1 on 2009-08-12
I am getting Ubuntu just the way I like it, it's coming along very nicely - I'm particularly thinking of things like the applications, the way I have compiz set to to inform rather than dazzle, the propritry drivers I need, and so forth.

So now I want to get it on my other computer.

I could work down the list of installed stuff side by side I suppose, but I was wondering if there was a better way? After all one of the big pluses of Ubuntu is that I can copy it around!

Now the hardware is not the same, so I am guessing that copying everything is not going to be a good idea (or is it?).

So what is the best way to go about this task? I'll settle for something that gets me pretty close, and I don't mind if it has to chug away for a long time to get there!

Thinking about it, and closely related - can I copy my existing install lock stock and barrel onto a bootable USB stick, for complete portability on a key ring?!

Nick

---

### Post by P4man on 2009-08-12
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by longtom on 2009-08-12
This might help you:

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Remastersys can be found in the repositories.

aaaargh - seconds to late....

---

### Post by P4man on 2009-08-12
Great minds think alike. But mine thinks faster lol 
;)

---

### Post by longtom on 2009-08-12
> **P4man said:**
> Great minds think alike. But mine thinks faster lol 
;)

Oh go away....it's my frills (ie additional text) that gave you the edge....*hmpf  :P

---

### Post by starbase1 on 2009-08-12
You know what I like best about Ubuntu?

It's the way I can ask how to do something that is near impossible in Windows, and a couple of minutes later some helpful person can give me an answer on how to do it in one line or even one word!

Thanks,
Nick

---

### Post by scouser73 on 2009-08-12
> **P4man said:**
> [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Also [[COLOR="Red"]**AptonCD**[/COLOR]]("http://aptoncd.sourceforge.net/").

---

### Post by Failbot on 2009-08-12
The only problem I ever have with cloning Ubuntu installs is with the proprietary video drivers. If you uninstall/disable them first then you can just clone the drive (using dd or similar), put cloned drive in the other computer and you're away. You can then install the appropriate proprietary video drivers for the new machine.

---

### Post by longtom on 2009-08-12
> **Failbot said:**
> The only problem I ever have with cloning Ubuntu installs is with the proprietary video drivers. If you uninstall/disable them first then you can just clone the drive (using dd or similar), put cloned drive in the other computer and you're away. You can then install the appropriate proprietary video drivers for the new machine.

This is an interesting thought.  How many clones have you done this way?

---

### Post by sinaisix on 2009-08-12
I would suggest you just copy your home folder onto a usb or external hdd. so when you install on the new pc all you do is to copy back your home forlder and you have all your settings and everything intact. You can also go to synaptic, click on file and choose save marked items to save all your marked installations to a usb or external hdd. on your new pc, allyou do is go to synaptic, click file and choose read markiings, pointing the dialogue box to where you saved the markings file. this will install all the apps you had on your first pc on the second one

---

### Post by burmanabhay88 on 2009-08-12
> **P4man said:**
> [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

> **starbase1 said:**
> You know what I like best about Ubuntu?

It's the way I can ask how to do something that is near impossible in Windows, and a couple of minutes later some helpful person can give me an answer on how to do it in one line or even one word!

Thanks,
Nick

Thanks for this great info. I had been looking for something like this for a long time. I had been using AptOnCd for creating my repositories but this seems to be a better option. Thanks again.

---

### Post by P4man on 2009-08-12
> The only problem I ever have with cloning Ubuntu installs is with the proprietary video drivers.


You can install binary (nvidia) drivers on a persistent live cd. Have a look here:

[http://klik.atekon.de/wiki/index.php/CustomizeUbuntuLive](http://klik.atekon.de/wiki/index.php/CustomizeUbuntuLive)

scroll down to the nVidia part. Worked like a treat for me, although I spent some time searching and understanding what the "/cow" thing was and how to enable it, and now I forgot LOL.  Think its just a kernel switch though, but don't quote me on that.

You can probably also change the script to accommodate ATI drivers as well, although its less of an issue as the opensource drivers are often good enough.

---

