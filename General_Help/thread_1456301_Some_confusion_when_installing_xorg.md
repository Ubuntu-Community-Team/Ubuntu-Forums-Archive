---
title: "Some confusion when installing xorg"
date: 2010-04-17
forum: General Help
---

### Post by cbecker78 on 2010-04-17
I have ubuntu server (8.04) installed on my old laptop now, and am trying to set up a graphical environment... I started with ```
sudo apt-get install xorg
``` and all seemed to be going well until I recieved a message that I needed to insert my 8.04 CD and press enter.   Is this normal to have to do that?  I didn't think the server CD even had anything to do with xorg.  Or does this indicate something is wrong with my install or repository setup?

I would just try to insert the CD and see what happens, but I accidentally left that in Dallas and it will be a few days before I am back there.  I really wanted to get this resolved over the weekend.

Thanks for any input~

---

### Post by marshmallow1304 on 2010-04-17
Check your /etc/apt/sources.list to see if there are any references to the CD there.  If so, comment them out, apt-get update, and try again.

---

### Post by cbecker78 on 2010-04-17
> **marshmallow1304 said:**
> Check your /etc/apt/sources.list to see if there are any references to the CD there.  If so, comment them out, apt-get update, and try again.

Hey, that is exactly it!  Can't believe I didn't think of that.

I also had to do "sudo aptitude update" before every-thing started downloading properly.  I'm not sure how that is different from "sudo apt-get update", but Hey, I am back in  buisness!  Thanks!

---

