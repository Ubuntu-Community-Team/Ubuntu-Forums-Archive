---
title: "Transmission overdownloading"
date: 2010-07-26
forum: General Help
---

### Post by Funkey Monkey on 2010-07-26
Hello I have a problem with the Ubuntu's default torrent client Transmission.

It seems to be overdownloading files. It usually is about 20mbs or so but today its like 100mbs for 17mbs I have. Please have a look at the printscreen below for details.

How can I fix this, should I be using another torrent client?

[IMG]http://i859.photobucket.com/albums/ab156/Genl_Smit/Screenshot-1.png[/IMG]

---

### Post by Vaphell on 2010-07-26
not that i don't think these numbers are weird, but maybe transmission counts only finished chunks as 'have' and there are lots of unfinished which don't count but affect total download, plus maybe overhead of the protocol is counted towards the total download too (though i doubt it)
check again when progress % is much higher (or even after torrent is finished) how things look, if the ratio of have/downloaded is still 1:5 then that's bad, if it is much closer to 1:1 then there is nothing to worry about.

---

### Post by marshmallow1304 on 2010-07-26
Does Transmission report hashfails?  It could be a poisoned torrent.

---

### Post by Funkey Monkey on 2010-07-28
I see that the screen shot uploaded previously did not show "Unverified" or "Corrupted" please refer to the new screen shot of another torrent, attached below.

[IMG]http://i859.photobucket.com/albums/ab156/Genl_Smit/Screenshot111.jpg[/IMG]

---

### Post by prodigy_ on 2010-07-28
Probably it just counts overhead traffic as "downloaded". In any case, if resulting files are ok (i.e. if they pass re-checking), there's nothing to worry about.

---

