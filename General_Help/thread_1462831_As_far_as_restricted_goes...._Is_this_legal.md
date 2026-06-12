---
title: "As far as restricted goes.... Is this legal?"
date: 2010-04-26
forum: General Help
---

### Post by schwabdale on 2010-04-26
Am I allowed to install Ubuntu on a system and install restricted drives to get DVD's and MP3's working and make a profit from that system?

---

### Post by mike555 on 2010-04-26
depends where you live , in the US it's probably not legal ... better to just include  an instruction on how people can easily install these themselves ...

---

### Post by pastalavista on 2010-04-26
> **schwabdale said:**
> Am I allowed to install Ubuntu on a system and install restricted drives to get DVD's and MP3's working and make a profit from that system?Yes you are, as long as the fee is for services. You can't sell the software, but you can charge for installing it.

---

### Post by mikewhatever on 2010-04-26
Restricted drivers have nothing to do with DVDs and mp3. The drivers are perfectly legal, just not free, while DVDs and mp3s need codecs, which must be purchased.

---

### Post by viralmeme on 2010-04-26
> **mike555 said:**
> depends where you live , in the US it's probably not legal ... better to just include  an instruction on how people can easily install these themselves ...

If schwabdale means the restricted codecs then even in the US it's probably not illegal. The law on this is a bit of a gray area as the holders of the alleged patents won't specify which ones and have never gone after anyone. They stick to making vague generalized threats. Reason being that if they went into court and their patent claims were proved false they would be unable to extort IP `royalties' from other companies.


`Microsoft claims that free software like Linux, which runs a big chunk of corporate America, violates 235'

[http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/](http://money.cnn.com/magazines/fortune/fortune_archive/2007/05/28/100033867/)

[http://www.groklaw.net/articlebasic.php?story=2010011422570951](http://www.groklaw.net/articlebasic.php?story=2010011422570951)

---

### Post by schwabdale on 2010-04-26
This is what I have to plug in to play DVD's..... What exactly am I doing? Is this legal to sell this Modification to Ubuntu?

                                 
[LIST=1]
[*][COLOR=#000000]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/COLOR]
[/LIST]
 [COLOR=#000000]      Next[/COLOR] [COLOR=#000000]      sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu[/COLOR]  [COLOR=#000000]      
Next[/COLOR] [COLOR=#000000]      sudo apt-get install libdvdcss2[/COLOR]  [COLOR=#000000]      Next[/COLOR] [COLOR=#000000]      sudo apt-get install w32codecs[/COLOR]

---

### Post by 3rdalbum on 2010-04-26
> **schwabdale said:**
> This is what I have to plug in to play DVD's..... What exactly am I doing? Is this legal to sell this Modification to Ubuntu?

                                 
[LIST=1]
[*][COLOR=#000000]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/COLOR]
[/LIST]
 [COLOR=#000000]      Next[/COLOR] [COLOR=#000000]      sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu[/COLOR]  [COLOR=#000000]      
Next[/COLOR] [COLOR=#000000]      sudo apt-get install libdvdcss2[/COLOR]  [COLOR=#000000]      Next[/COLOR] [COLOR=#000000]      sudo apt-get install w32codecs[/COLOR]

No, it's not legal anywhere (as far as I know). W32codecs are Microsoft's property. You're allowed to use them if you have Windows, but not without.

libdvdcss2 is on possibly shaky legal grounds in many places due to it cracking an encryption scheme.

However, it's perfectly legal to install Fluendo's MP3 decoder and Fluendo's DVD playback software; the latter is commercial software that you must purchase. Or use PowerDVD Linux, but I believe it's unmaintained; it's only for 8.04 and doesn't even work on 64-bit. How archaic is that?!

Come to think of it, Fluendo has something similar to w32codecs, but legal to install; it's also purchasable software.

---

### Post by schwabdale on 2010-04-26
Thanks for the reply. Question: 
So, what if I did everything except the last two lines.....
[COLOR=#000000]Next[/COLOR] [COLOR=#000000]      sudo  apt-get install libdvdcss2
[/COLOR][COLOR=#000000]Next[/COLOR]  [COLOR=#000000]      sudo apt-get install w32codecs

Maybe I could have instructions for the end user to install this themselves?
Would that be legal?
[/COLOR]

---

