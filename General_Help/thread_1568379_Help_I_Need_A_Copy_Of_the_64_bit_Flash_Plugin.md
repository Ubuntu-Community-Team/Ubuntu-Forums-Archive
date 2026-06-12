---
title: "Help: I Need A Copy Of the 64 bit Flash Plugin"
date: 2010-09-05
forum: General Help
---

### Post by Mark76 on 2010-09-05
I removed the one I had because of some security alert. But lots of sites don't work with the 32 bit one with the wrapper so I'd like it back.

Can anyone point me to a place I can download it?

---

### Post by dcstar on 2010-09-05
> **Mark76 said:**
> I removed the one I had because of some security alert. But lots of sites don't work with the 32 bit one with the wrapper so I'd like it back.

Can anyone point me to a place I can download it?

Please use the Forum Search before asking questions:

[http://ubuntuforums.org/showpost.php?p=9478720&postcount=3](http://ubuntuforums.org/showpost.php?p=9478720&postcount=3)

---

### Post by colin.p on 2010-09-05
I think you may have misunderstood what the OP asked. I take it he already had the last version of 64 bit flash, but was now told that it is a security threat and to update to a newer version. However, there is no newer version of flash 64.
I use the program flash-aid and it installed the 32bit flash. I don't see any difference as of yet, beyond the fact that I find flash to be buggy at the best of times.

Now that I re-read the OP's question and the reply, it appears I misunderstood the original question. Apologies all around. I will now slink back to my rock.

---

### Post by Mark76 on 2010-09-05
AHA! It's not the plugin after all.

There's something screwy about BBC embedded media in 64 bit Linux.

I've tried it with Gecko and Webkit browsers

---

### Post by ellgor on 2010-09-05
Hi,

Found this guide that got mine working great try this:

The easiest and safest way to install Flash 64 bit on Ubuntu is to use the ppa.

Note: When I did this it removed a whole bunch of things (around 80) nothing seems to have been affected five days on.

1. Remove your current flash install if you have it:
Code:

sudo aptitude remove flashplugin-installer

2. Add the ppa to your sources list. There are several ways to do it so choose your favourite, but to use command line do this:
Code:

sudo add-apt-repository ppa:sevenmachines/flash

3. Update apt and install Flash 64 bit:
Code:

sudo aptitude update
sudo aptitude install flashplugin64-installer

4. Restart Browser

It got mine working a treat.

Regards, Ellgor.

---

