---
title: "processing logs me out of x"
date: 2010-06-17
forum: General Help
---

### Post by triss on 2010-06-17
hi all,

i'm attempting to run processing (from processing.org) on ubuntu 10.4 32bit but a experiencing crashes.

this is currently installed along side sun java from the partners repositories.

with fglrx installed launching any processing sketch will log me out of ubuntu desktop entirely.

with the open source graphics drives every thing works for a while and then i'm logged out of X at a random point.

I've just turned off visual effects as suggested here: [http://processing.org/discourse/yabb2/YaBB.pl?num=1271869958/0#9](http://processing.org/discourse/yabb2/YaBB.pl?num=1271869958/0#9) in the hope things will be more stable.

can any one suggest a work around for this or explain why it is happening?:confused:

Cheers,
tris

---

### Post by bobonthenet on 2010-06-29
I don't suppose you have found a solution for this have you?  I'm having the exact same issue.

---

### Post by Don Barzini on 2010-06-29
Many people have experienced a "random logout" problem with 10.04. It seems there is a bug with xorg and a bug report has been filed.

I had the problem myself on one machine. The only thing that fixed it was a patch by a guy named Bryce Harrington who I think is an Ubuntu developer.

If you want to try the fix the command is below, but it is not an "official" Ubuntu repository.

In a terminal window run....

```
sudo add-apt-repository ppa:bryceharrington/purple && sudo apt-get update && sudo apt-get upgrade
```

Then reboot the machine.

Good Luck.

---

### Post by triss on 2010-07-01
I&#8217;ve had no real problems since turning off Desktop effects. I&#8217;m still using the open source driver. Only issue is that it doesn&#8217;t quite perform as quickly in this setup as it did under Windows. (I&#8217;m doing 2D stuff with lots of transparency, I&#8217;m not sure how well my 3D stuff is working).

I haven&#8217;t tried Don Barzini&#8217;s suggestion yet. One other thing I&#8217;m tempted to do is to try the new version of the ATI/AMD drivers (version 10.06 I think) that have just been released in the hope that they work.

Anyone have any experience with this?

Has Don's suggestion worked for you?

---

