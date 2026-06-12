---
title: "convert gif to images"
date: 2012-03-16
forum: General Help
---

### Post by conradin on 2012-03-16
Hi all, 
i want to convert an animated gif into a series of images. Im almost certian the convert command from the imageMagick suite can handle this conversion, but I dont know how to do the command. Can any one help me out with this?

---

### Post by mraandtux on 2012-03-16
Seach on the web, and you'll know how!

---

### Post by conradin on 2012-03-16
sometimes I REALLY wish the etiquette guide lines for this site where equivalent to 4chan. -- I have searched the interwebz, and Im still not there yet.

---

### Post by mcduck on 2012-03-16
> **conradin said:**
> sometimes I REALLY wish the etiquette guide lines for this site where equivalent to 4chan. -- I have searched the interwebz, and Im still not there yet.

They are probably much better. But sadly that doesn't mean everybody would actually read and respect them. :/

Anyway, something like this should work if you know how many frames the GIF has:
```
convert 'images.gif[0-3]' images.jpg
```

---

### Post by conradin on 2012-03-16
Thanks McDuck, That totally worked!

---

