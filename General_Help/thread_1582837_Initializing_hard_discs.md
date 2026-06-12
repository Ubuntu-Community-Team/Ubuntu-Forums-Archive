---
title: "Initializing hard discs???"
date: 2010-09-27
forum: General Help
---

### Post by dougalkerr on 2010-09-27
I bought an eSata enclosure and disc to go with it.
When I first tried to use it I couldn't get the thing to do anything even though the system could 'see' the drive.
I looked in 'Disk Utility' and it was there but, I couldn't apparently work with the drive.

I have a couple of questions now that I have the drive working...

I initialized the drive using (ahemmm...) Windows coz I don't have the Linux know-how to do this and besides I didn't know it was needing initialized till I used the Microsoft environment to see if Windows could pick up and use the drive. Initially it couldn't but, I did see an option to Initialize the drive - which I did. I could then work with the drive, format it, etc...

I went back to Ubuntu and Hey Presto the drive could be seen. I had to them mount it 'once' and have been able to work with it since. (There are posts about having to add lines to fstab after finding out the UUID of the divice and so on but, I have not needed to do this). If it appears unmounted for any reason - I mount it, simple.

So, my questions;

Why does Ubuntu not appear to have an option flagged to initialize the new drive? Did I miss it in Disk Utility?
Why is it that after editing fstab by adding lines suggested in an earlier post I then could not mount the drive at all. I commented out the lines, saved the fstab file again and rebooted to find the drive now available again - although I did have to mount it.
What is the proper way to automount an eSata drive?

Thanks.

---

### Post by dougalkerr on 2010-10-16
Any takers on this???

---

### Post by dougalkerr on 2010-10-19
Anybody???

---

### Post by sikander3786 on 2010-10-19
Hi.

> 
Why does Ubuntu not appear to have an option flagged to initialize the new drive? Did I miss it in Disk Utility?

If I remember correctly, gparted has got that ability. Can't check it right now.

> Why is it that after editing fstab by adding lines suggested in an earlier post I then could not mount the drive at all. I commented out the lines, saved the fstab file again and rebooted to find the drive now available again - although I did have to mount it.

Might be the syntax was not correct. Can you post that and also the UUID of your drive so we can have a look at it.

> What is the proper way to automount an eSata drive?

Depends on the filesystem. The proper way is still the fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

