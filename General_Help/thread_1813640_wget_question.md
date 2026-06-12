---
title: "wget question"
date: 2011-07-28
forum: General Help
---

### Post by thunderbirdje on 2011-07-28
Hello,

I want to try to download an image of the earth with wget located at [http://static.die.net/earth/mercator/1600.jpg](http://static.die.net/earth/mercator/1600.jpg) which is refreshed every 3 hours and set is as a wallpaper (for whom is interested details [here]("http://lifehacker.com/5556316/set-a-rotating-picture-of-the-earth-as-your-ubuntu-wallpaper")).

Wen I fetch the file with ```
wget -r -N http://static.die.net/earth/mercator/1600.jpg
``` the jpeg is only 37 bytes and of course too small and not readable.

What do I wrong?

Thank you for helping out!

---

### Post by An Sanct on 2011-07-28
It seems, that what you can download is a GIF file, probably 1*1 white pixel :) simply said, it is some sort of hotlinking protection. I guess you are not the only one, who would like to do something like that and they know it.

---

### Post by An Sanct on 2011-07-28
what about this site? [http://ashtokalo.wordpress.com/2010/06/17/world-sunglight-map/](http://ashtokalo.wordpress.com/2010/06/17/world-sunglight-map/)

---

### Post by An Sanct on 2011-07-28
LOL :) you user agent is Santa ... nice one :)

---

### Post by thunderbirdje on 2011-07-28
So great! Thank you all for helping me out!!! It's such a great picture as a wallpaper! Santa :guitar:!

---

