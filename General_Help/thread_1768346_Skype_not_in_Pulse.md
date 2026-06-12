---
title: "Skype not in Pulse"
date: 2011-05-26
forum: General Help
---

### Post by craig100 on 2011-05-26
Hi,

After recovering from today's Skype crash by doing this 

cd /usr/lib32
sudo chmod ugo-r libpulse.so.0.12.2
sudo chmod ugo-r libpulse-simple.so.0.0.3

from post [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646862](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/646862)

and then this

mv ~/.Skype/shared.xml ~/.Skype/shared~.xml

from post [http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/?utm_source=rss&utm_medium=rss&utm_campaign=skype-crashed-today-heres-a-fix](http://www.omgubuntu.co.uk/2011/05/skype-crashed-today-heres-a-fix/?utm_source=rss&utm_medium=rss&utm_campaign=skype-crashed-today-heres-a-fix)

I now find that Skype doesn't appear in Pulse Audio Volume Control so I can't redirect it to my headset.

Also if Pulse Audio Volume Control is open, then I get "Problem with Audio Playback" message if I try a test call.

Any clues where to look?

Cheers,

Craig

---

### Post by craig100 on 2011-05-27
Ok, so I executed those two initial commands from a blog post and didn't really understand them. Now I do, I've reversed them by changing the "-" to a "+" and it now all works....Phew!  

There's a lesson there somewhere.:D

---

