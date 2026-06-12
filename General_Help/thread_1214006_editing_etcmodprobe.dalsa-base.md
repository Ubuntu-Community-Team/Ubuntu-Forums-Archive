---
title: "editing /etc/modprobe.d/alsa-base"
date: 2009-07-15
forum: General Help
---

### Post by asamay81 on 2009-07-15
hi
i was trying to solve my sound problem using this how to
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

my desktop sound problem is still unresolved in the board
[http://ubuntuforums.org/showthread.php?t=1190144](http://ubuntuforums.org/showthread.php?t=1190144)
[http://ubuntuforums.org/showthread.php?t=1187055](http://ubuntuforums.org/showthread.php?t=1187055)

when i was trying to edit  /etc/modprobe.d/alsa-base file i was getting  a file like this
[IMG]http://img32.imageshack.us/img32/4959/screenshotsdp.png[/IMG]
[IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://img32.imageshack.us/img32/4959/screenshotsdp.png%5B/IMG%5D[/IMG]

there is no data in the file. is it possible?

thanks

---

### Post by t4thfavor on 2009-07-15
It's now alsa-base.conf I put both files in there just for good luck :) I now only have an issue with headphones, all else works.

---

### Post by jocko on 2009-07-15
> **asamay81 said:**
> hi
i was trying to solve my sound problem using this how to
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

my desktop sound problem is still unresolved in the board
[http://ubuntuforums.org/showthread.php?t=1190144](http://ubuntuforums.org/showthread.php?t=1190144)
[http://ubuntuforums.org/showthread.php?t=1187055](http://ubuntuforums.org/showthread.php?t=1187055)

when i was trying to edit  /etc/modprobe.d/alsa-base file i was getting  a file like this
[IMG]http://img32.imageshack.us/img32/4959/screenshotsdp.png[/IMG]
[IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://img32.imageshack.us/img32/4959/screenshotsdp.png%5B/IMG%5D[/IMG]

there is no data in the file. is it possible?

thanks

That's because there is no "alsa-base" file anymore. It's been renamed to "alsa-base.conf".

---

### Post by asamay81 on 2009-07-15
thanks for the replies :)...i understood the reason...one more help

search for ALC880 in ALSA-configuration.txt resulted these outputs

    ALC880
      3stack    >>  3-jack in back and a headphone out
      3stack-digout    >>  3-jack in back, a HP out and a SPDIF out
      5stack   >>   5-jack in back, 2-jack in front
      5stack-digout    >>  5-jack in back, 2-jack in front, a SPDIF out
      6stack    >>  6-jack in back, 2-jack in front
      6stack-digout    >>  6-jack with a SPDIF out
      w810        >>  3-jack
      z71v        >>  3-jack (HP shared SPDIF)
      asus       >>   3-jack (ASUS Mobo)
      asus-w1v    >>  ASUS W1V
      asus-dig    >>  ASUS with SPDIF out
      asus-dig2   >>   ASUS with SPDIF out (using GPIO2)
      uniwill    >>  3-jack
      fujitsu   >>   Fujitsu Laptops (Pi1536)
      F1734        >>  2-jack
      lg       >>   LG laptop (m1 express dual)
      lg-lw        >>  LG LW20/LW25 laptop
      tcl        >>  TCL S700
      clevo       >>   Clevo laptops (m520G, m665n)
      medion    >>  Medion Rim 2150
      test        >>  for testing/debugging purpose, almost all controls can be adjusted.

i am confused to choose my model..windows sound manager is this one 
[IMG]http://img17.imageshack.us/img17/6151/64907693.jpg[/IMG]
now which model can i choose? is it 6stack?

---

### Post by t4thfavor on 2009-07-15
Looks like a 6 stack. Im never sure though. This is something about Ubuntu that needs work.

---

