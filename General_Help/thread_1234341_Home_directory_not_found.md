---
title: "Home directory not found"
date: 2009-08-07
forum: General Help
---

### Post by DUKANE on 2009-08-07
I have an Asus Eee 900A with Ubuntu NBR 9.04 installed. When I installed the system, I made one partition on the internal SSD and mounted as /. I left 32 MB for swap space. I mounted the /home directory to a 16GB SD card installed in the memory card reader.

Although not exact, here is basically my /etc/fstab file:
/dev/sda1     /         ext4       defaults      0         1
/dev/sdb1     /home     ext4       defaults      0         0

But when I start up, I get the following error message:
Your home directory is listed as: '/home/tim' but it does not appears to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

If I log in with a fail safe session, and then edit my fstab file, or even just open it without a modification, and then restart the computer (without powering down) then it will work. But if I power the computer down, it goes back to the error message. When I am able to get the system started, I can see that the /home directory is in fact where it belongs and it's all there.

Any ideas what could be wrong or how I could fix this?? Thank you!

---

### Post by dcstar on 2009-08-07
> **DUKANE said:**
> I have an Asus Eee 900A with Ubuntu NBR 9.04 installed. When I installed the system, I made one partition on the internal SSD and mounted as /. I left 32 MB for swap space. I mounted the /home directory to a 16GB SD card installed in the memory card reader.

Although not exact, here is basically my /etc/fstab file:
/dev/sda1     /         ext4       defaults      0         1
/dev/sdb1     /home     ext4       defaults      0         0

But when I start up, I get the following error message:
Your home directory is listed as: '/home/tim' but it does not appears to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

If I log in with a fail safe session, and then edit my fstab file, or even just open it without a modification, and then restart the computer (without powering down) then it will work. But if I power the computer down, it goes back to the error message. When I am able to get the system started, I can see that the /home directory is in fact where it belongs and it's all there.

Any ideas what could be wrong or how I could fix this?? Thank you!

Do not use /dev designations (these can change), use an UUID - do a search on details on how to set things up.

Also it is possible that the SD card is not initialised quickly enough in the boot up process, so it may not be available when it is required.

---

### Post by DUKANE on 2009-08-07
Hi David,
Thank you for your reply! I had the UUID's in there, and had the same problem. I changed to the /dev/sdb1 as part of my trials to getting it to work. I had the same problem with both setups.

I did find a solution to my problem however in between posting and now as I continued my troubleshooting. In the memory card, under the root directory was the folder "tim". What I did was create a new folder "home" and then move "tim" under "home". This seems to have corrected the issue, the system now logs in with all of my settings each time. I suppose alternatively I could have also changed my HOME environment variable to point just to "tim" instead of "home/tim", probably would have had the same effect.

---

### Post by DUKANE on 2009-08-08
Looks Like I Spoke Too Soon Yesterday As I Woke Up This Morning And Experienced Exactly The Same Problem. I Checked The File System On The Memory Card And Everything Is There. I Changed Back To The UUID In The fstab But There Was No Change. Tried Changing The HOME Environment Variale But Also Got The Same Results..........

---

### Post by DUKANE on 2010-06-13
I know this is old, but I wanted to post a followup for anyone interested or having a similar problem.

The problem has been corrected by upgrading to 10.04. There is no longer any problem with the OS detecting the "alternative" location of my /home directory.

---

