---
title: "In tty1 I see no block devices found 4x why is that?"
date: 2009-07-07
forum: General Help
---

### Post by simudream on 2009-07-07
[IMG]http://www.flickr.com/photos/26389252@N05/3698344085/[/IMG] [http://www.flickr.com/photos/26389252@N05/3698344085/]("http://www.flickr.com/photos/26389252@N05/3698344085/")

Above is a pic of the problem

In tty1 I see no block devices found 4x, why is that?

After booting up and I switch to tty1 with control alt F1 I see this, this must be something to do with the problem other people are reporting about fake raid, I'm using a promise raid controller and have 2 mirrored drives running with dmraid. I'm using them and they seem to be working just fine. I would just like to know what this error message is all about, thanks.

---

### Post by ronparent on 2009-07-08
It doesn't sound like you really have a problem. Try the command **blkid** in a terminal. This should reveal your block devices. Likewise, entering the command sudo **dmraid -r** should list your raid devices.

---

