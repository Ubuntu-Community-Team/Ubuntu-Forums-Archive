---
title: "Linux won't use swap file after rebooting"
date: 2010-08-17
forum: General Help
---

### Post by Phillip Bromley on 2010-08-17
I'm having problems using a swap file to increase swap space in Linux. I followed the instructions for creating a swap file, as shown here:

[http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space]("http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space")

It works, and I increased my swap space. But when I reboot, I'm back to the original amount of swap space I had before. The swap file I created is still there, but it's not being used as swap space. I tried remounting the swap file but it doesn't work.

Also, it seems there isn't an fstab entry created for the swap file. Strange, huh? I don't think it made a difference but I manually copied the UUID for the swap file and made an entry in fstab.

I may be wrong, but from what I can tell the UUID of the swap file keeps changing every time I reboot.

So basically every time I reboot I have to repeat the instructions shown above to get more swap space.

Does anybody know what's going on here?

---

### Post by Phillip Bromley on 2010-08-17
Bump

---

### Post by earthpigg on 2010-08-17
> The swap file I created is still there, but it's not being used as swap space. I tried remounting the swap file but it doesn't work.

can you give us more in-depth details about these two sentences?

ie: are you sure it needs to be using that swap space? is an error message indicating to you that it isn't working, or something else?

---

### Post by Phillip Bromley on 2010-08-17
I used this command to create the swap file, as indicated in the link in my opening post:

*dd if=/dev/zero of=/swapfile bs=1024 count=1048576*

I don't get any error messages, but I know I need swap space because Firefox crashes when I open too many tabs or too many pages are loading at once, etc. I opened the system monitor and I noticed I only have 106MB of swap space, and that almost always 100% of it is being used.

When I follow the instructions as mentioned above, they work. My swap space is increased, but when I reboot, I'm back to 106MB of swap space. So basically, I'm having trouble making the swap space permanent. I don't know what's causing the OS to stop using the file as swap space when I reboot.

---

### Post by Phillip Bromley on 2010-08-17
bump

---

### Post by wojox on 2010-08-17
Here [How do I add more swap?]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?")

You've already created the *file* now add it.

---

### Post by Phillip Bromley on 2010-08-17
I'll try that and see how it works out. Thanks!

---

