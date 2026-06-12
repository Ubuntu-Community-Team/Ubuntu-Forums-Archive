---
title: "download image works with httrack but not with wget or curl"
date: 2012-03-13
forum: General Help
---

### Post by ohnonot on 2012-03-13
hello,
i have a script to download an image once an hour to put it on my desktop.
i'm using httrack for that but it feels like catching flies with cannonballs...

it seems wget or curl would be the best choice but it does not work.

this one works:```
httrack -T30 -R10 --get http://static.die.net/earth/mollweide/1024.jpg
```and all of those don't:```
wget --output-document=1024.jpg "http://static.die.net/earth/mollweide/1024.jpg"
curl -o 1024.jpg http://static.die.net/earth/mollweide/1024.jpg
wget http://static.die.net/earth/mollweide/1024.jpg
```- everytime it downloads only 37 bytes, saying it's image/gif.

it's not a big problem but i'd like to solve it.

any help? thanks.

---

### Post by miklcct on 2012-03-13
Try to use different HTTP headers to download it. wget should let you change some of the options.

---

### Post by ohnonot on 2012-03-13
i've been randomly throwing command line switches for a while but it seems all i ever get is this:```
HTTP request sent, awaiting response... 200 OK
Length: 37 [image/gif]
Saving to: `1024.jpg'

```- ???

---

