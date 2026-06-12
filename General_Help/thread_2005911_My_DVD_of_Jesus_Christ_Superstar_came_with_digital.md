---
title: "My DVD of Jesus Christ Superstar came with digital download offer, software not work"
date: 2012-06-18
forum: General Help
---

### Post by MechaMechanism on 2012-06-18
My DVD of Jesus Christ Superstar came with digital download offer, software not working.

There is a promo code on the DVD packaging for a free download of the movie.  You go to the movie studio web site and enter promo code and then it prompts you with some software to install.  The software seems to work fine in wine, but then when I go to run it, it never seems to accept the code.

It just says: Cannot acquire license for the requested files. Please try again later.

Any of you have any experience with this sort of thing, Google didn't really return any results to my satisfaction.  I mean it's not any big loss or anything since I can always use handbrake.  I just wanted to see what it was like.  Thanks for any help you can offer.

---

### Post by dodo3773 on 2012-06-18
I am no expert on this by any means but it has been my experience that not all wine applications can make tcp conections without using stunnel or reverse engineering the applications libraries to some extent. The former being the easier of the two of course. As with most things though there has got to be another way. Still my guess is that the application cannot access the internet.

---

### Post by dcottingham on 2012-06-18
Here's a guess. The download may involve Windows Media Player DRM, and I believe I've heard that WMP's license handling software has been carefully designed by Microsoft to not work under wine. Something to do with checksumming every dll it uses.

---

### Post by nothingspecial on 2012-06-18
I had something similar with Columbia Records. The sticker on the cover that offered the digital download made no mention of needing a particular operating system.

A few emails, phone calls and threats worked in the end :)

---

### Post by MechaMechanism on 2012-06-18
I'll just keep working at it then.

---

