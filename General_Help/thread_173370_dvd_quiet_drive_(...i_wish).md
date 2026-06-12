---
title: "dvd quiet drive (...i wish)"
date: 2006-05-10
forum: General Help
---

### Post by ruzle0 on 2006-05-10
hi i have a pioneer dvd drive [type 109 firmware 1.58] and when watching a film with it, it's hammering away as fast as its little motor and laser beams will allow. 
not only is this noisy [enough in itself to be a problem] but every now and then it gets ahead of itself it spins down, ...then you guessed it, not up fast enough again to prevent a small blip in the film.

i have downloaded a win app quietdrive by pioneer, and ran it in an old w2k install, in the hope of changing the read speeds but the utility won't detect the drive, dispite the dvd drive working as expected. [quitedrive gives the option to save settings to the drive so should cover me in linux]

I have searched around the net using various phrases but have come up with no leads. Is anyone aware of a way to limit the dvd read speads through the OS in Ubuntu

---

### Post by gibson on 2006-05-10
Try these, although i am not sure how good they are

[http://www.ubuntuforums.org/archive/index.php/t-78754.html](http://www.ubuntuforums.org/archive/index.php/t-78754.html)

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=h/hdparm](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=h/hdparm)

all i know really, it appears the **hdparam** command is what you need. 


Sorry its how much help, should put you on the right track though.

Let me knows how it goes

g

---

### Post by ruzle0 on 2006-05-10
I've set hdparm -E8 /dev/hdc [read x8 speed] and that seems to give the effect i'm after, and hopefully nothing else.
Thanks for the pointer, it was something like this i was hoping i'd stumble accross on the net.
Cheers for that
Russell

---

