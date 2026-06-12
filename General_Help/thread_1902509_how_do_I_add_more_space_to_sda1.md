---
title: "how do I add more space to sda1"
date: 2011-12-30
forum: General Help
---

### Post by pretty_whistle on 2011-12-30
I'm trying to add 20GB of space to the main sda1 drive/partition.

I used a boot CD of gparted and still couldn't add more space to the main sda1 drive/partition.  When I tried to extend it by 20GB, it kept having some error saying it failed.

The 20GB drive I have I deleted its partition and  that left it unallocated.  But to the best of my recall it can't be unallocated when you're trying to do this.

Why isn't this letting me do this?  I'm doing something wrong but can't figure out what.

On windows I know how to do it, but here..??

Maybe I've forgotten a step?

---

### Post by xyzzyman on 2011-12-30
Is the 20GB of unallocated space directly after SDA1?

---

### Post by dRounse on 2011-12-31
Try formatting the 20GB to the format of the rest of the hard drive.

---

### Post by Paqman on 2011-12-31
Are there any lock symbols showing up on Gparted next to partitions? One thing the LiveCD does is to find and mount any swap partitions to improve performance, but if the swap is located within an extended partition it will cause the whole extended to be locked.

Right click on your swap and "swapoff", then you should be able to shrink the adjacent partition and expand your other one.

---

### Post by pretty_whistle on 2011-12-31
> **xyzzyman said:**
> Is the 20GB of unallocated space directly after SDA1?
Yes it is.


> **dRounse said:**
> Try formatting the 20GB to the format of the rest of the hard drive.
Already did that.


> **Paqman said:**
> Are there any lock symbols showing up on Gparted  next to partitions? One thing the LiveCD does is to find and mount any  swap partitions to improve performance, but if the swap is located  within an extended partition it will cause the whole extended to be  locked.

Right click on your swap and "swapoff", then you should be able to  shrink the adjacent partition and expand your other one.
I don't see any locks but I'll try that.

---

### Post by Elfy on 2011-12-31
If you still get issues - try a screenshot for us.

---

### Post by pretty_whistle on 2011-12-31
> **Paqman said:**
> Are there any lock symbols showing up on Gparted next to partitions? One thing the LiveCD does is to find and mount any swap partitions to improve performance, but if the swap is located within an extended partition it will cause the whole extended to be locked.

Right click on your swap and "swapoff", then you should be able to shrink the adjacent partition and expand your other one.
The swap is already off.

Shrink the adjacent partition and expand sda1?  Wouldn't that just leave me with sda3 smaller but not 'gone'?

---

### Post by pretty_whistle on 2011-12-31
> **forestpiskie said:**
> If you still get issues - try a screenshot for us.
How do I take a screenshot when I'm working off of a boot CD?

---

### Post by Quackers on 2011-12-31
The same way you would from an installed system :-)  With the "take screenshot" utility.

---

### Post by Elfy on 2011-12-31
If there's no screenshot tool - use the PrtSc button - that should still work - depends what boot cd it is. 

Last time I used the gparted one I think you could get a f/fox going. Might have been partedmagic though ...

---

### Post by Quackers on 2011-12-31
Oh dear, I didn't read your first post properly :-(  My apologies, pretty_whistle.
If you boot from the Ubuntu cd/usb and select "try Ubuntu" you can have all the tools available to you and you can re-arrange partitions, as long as swap is turned off.

---

### Post by pretty_whistle on 2011-12-31
> **Quackers said:**
> Oh dear, I didn't read your first post properly :-(  My apologies, pretty_whistle.
If you boot from the Ubuntu cd/usb and select "try Ubuntu" you can have all the tools available to you and you can re-arrange partitions, as long as swap is turned off.
I wonder if what you said would work better than a boot CD of parted.

---

### Post by pretty_whistle on 2011-12-31
I used my boot gparted boot CD and I saw a screenshot utility and used it.  It claimed it put the screenshots in "root" but when I went there but there are no screenshots saved.

I think I'll try "try ubuntu" method.

---

### Post by Quackers on 2011-12-31
It should be a little more straightforward.

---

### Post by pretty_whistle on 2011-12-31
It worked!  Yes!!

When trying to resize sda1 I just didn't push the slider all the way-I left 1 MB of free space at the end of it.  Either this is why it worked finally and/or doing the "Try Ubuntu" method.

---

### Post by Quackers on 2011-12-31
I'm glad that things are working now :-)
Happy New Year to you :-)

---

### Post by pretty_whistle on 2011-12-31
> **Quackers said:**
> I'm glad that things are working now :-)
Happy New Year to you :-)
Happy New Year to you and everyone here!  :D

---

### Post by vpharry on 2011-12-31
Ya... Happy new year to everyone

---

