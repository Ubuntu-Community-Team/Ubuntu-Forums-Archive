---
title: "Is there a better solution for dual screen?"
date: 2012-03-26
forum: General Help
---

### Post by Spewed on 2012-03-26
Is there a better solution for Dual Screen monitors than Nvidia X Server Settings? I mean, the support with this program is just absolutely ATROCIOUS. You should be able to simply select what you want and have it happen. However, in my case when I connect my television and select "Twin View". It always jumples the screen up and freezes, then I have to restart and do it again. Usually it works, but sometimes it takes another restart for it to work. After that, if I decide to disconnect the monitor at any time(I do that frequently as I only use dual monitors for certain tasks. Then when I log out and boot back up I get this configuration load error, and am stuck with no shell. Then I have to open up Nvidia X Server Settings and mess around with things. Then log out and log back in again a few more times for it to work. 

This is ridiculous. Anyone know of any better solutions.

---

### Post by whatthefunk on 2012-03-26
That is crazy.  I use a program called autorandr to switch between dual screen and single screen.  It saves monitor configuration settings so that you can easily recall them.  Im not sure if it would help you though as it still relies on the nVidia x server settings.

---

### Post by Spewed on 2012-03-26
> **whatthefunk said:**
> That is crazy.  I use a program called autorandr to switch between dual screen and single screen.  It saves monitor configuration settings so that you can easily recall them.  Im not sure if it would help you though as it still relies on the nVidia x server settings.


Maybe it will benefit me. How do you call upon a saved monitor configuration in X Server Settings?

---

### Post by whatthefunk on 2012-03-26
You can download the program from here:
[https://github.com/wertarbyte/autorandr](https://github.com/wertarbyte/autorandr)

You dont have to install or anything, just save it all in a recognized PATH, like in a bin folder in your home directory.

Once its in there, you can type "autorandr --help" to see the options.

```
autorandr -s PROFILENAME
```

This should save a profile.  Save your single screen profile under a name like "single," manually change to dual monitor mode, and then save your dual screen profile under a name like "double."  Then you can recall them esily without having to tweak settings all the time.

Like I said though, your problem sounds like a problem with nvidia and since autorandr relies on nvidia x server settings, this may not do anything for you.  Worth a shot though I guess....

---

### Post by Adrian98 on 2012-03-26
I have also used autorandr  for switching between dual screen !! I think it may help !! :p

---

### Post by Spewed on 2012-03-26
> **Adrian98 said:**
> I have also used autorandr  for switching between dual screen !! I think it may help !! :p

I'm going to have to try then. Thanks.

---

