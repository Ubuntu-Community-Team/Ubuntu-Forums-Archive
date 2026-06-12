---
title: "&quot;Make Startup Disk&quot; options grayed out !"
date: 2010-08-08
forum: General Help
---

### Post by skbhat03 on 2010-08-08
Dear All,

I am trying to make a startup disk; i have inserted 4GB pen drive, correctly formated.
When i go to *System>Administration>Startup Disk Creator* i can see the everything, but options "Stored in reserved extra space" etc are all grayed out.
I have attached a screenshot, hope it helps in explaining my problem.
Can someone please help me in getting these options enabled?

My OS is Ubuntu 10.04

Thanks & Best regards,
Subbu.

---

### Post by Peter7K on 2010-08-09
Same problem.  I was reading somewhere that they switched around 10.04 "bootability" from usb, but I thought they merely moved the option when you startup with it (the option to go into the USB's version of ubuntu)

---

### Post by evlev on 2010-08-11
Same problem here,
Thing is, I was able to use the same USB sticks, a couple of weeks ago, and now they stopped working, WTF?
My USB sticks are of the SanDisk Cruzer variety.

---

### Post by howefield on 2010-08-11
Could be this...

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/557775](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/557775)

See post 4 for possible workaround.

---

### Post by Peter7K on 2010-08-12
Awesome thank you sir.  Don't know why that bug didn't come up when I searched... oh well.

---

### Post by howefield on 2010-08-12
Yep, looks like we need usb-creator version 0.2.23

---

### Post by hydrox24 on 2010-11-30
I thought I'd Just post the Workaround mentioned in the link above here to make things a bit more convenient for people having the same issue.

> I came up with a workaround:

Copy your ISO image to /tmp or somewhere else not automatically destected by usb-creator.

Choose 'Other' and select that ISO

Select that image from the listing

Now it's not greyed out anymore and you can also go back to select your original image and it will be good.

Voilá!

To Paraphrase:

1- Move the Automatically appearing .ISO from where it is to a different folder (Doesn't matter where, but the desktop worked for me)

3- open up the USB creator and click "other" for the source, navigate to the folder the ISO is in and select it.

4- JOB DONE!

---

### Post by schlatter on 2012-05-13
I still have this problem in 12.04 and the described work-around does not work for me. Anybody else having this issue?

---

### Post by Hanashimaru on 2012-11-07
I tried the workaround and it didn't work for me either.

---

### Post by wildmanne39 on 2012-11-07
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

