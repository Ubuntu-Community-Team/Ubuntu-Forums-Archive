---
title: "Expanding Ubuntu Partition"
date: 2011-03-03
forum: General Help
---

### Post by Reynbow on 2011-03-03
I'm still quite nooby when it comes to this Ubuntu stuff and am not quite sure how to go about what I want to do.

I had Windows 7 installed on this computer,
Then installed Ubuntu (Dual boot)
And have now formatted and deleted the Windows partition and would like to expand the Ubuntu partition to take up the wasted space.

How would I go about what I would like to do.
Here's a screenshot of the GParted window;

[IMG]http://img.photobucket.com/albums/v633/Sting81/Screenshot.png[/IMG]

Any help appreciated <3

---

### Post by mikewhatever on 2011-03-04
You have to expand the extended partition (/dev/sda2) first, then expand the Ubuntu partition (/dev/sda5). It can only be done from a live cd/usb, because when Ubuntu is running those partitions are in use and can't be modified.

---

### Post by Reynbow on 2011-03-04
Okay cool, thankyou for that. I wouldn't have known to expand dev/sda2 first. 
I ended up making a GParted USB thing, booted into that and did it that way.
Thanks for the help =]

---

