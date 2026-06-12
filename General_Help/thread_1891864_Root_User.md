---
title: "Root User"
date: 2011-12-06
forum: General Help
---

### Post by TheTinyt1 on 2011-12-06
Not really sure where to start this thread.

I am using Ubuntu 11.10 64 bit on an Intel® Celeron(R) CPU E1400 @ 2.00GHz × 2 emachine with 2 gig ram. It is running great better than the 32 bit version of the same software. 

My problem is this. I want to know how to set myself up so that I can access all the directories in my machine. For instance I want to add some jpg files to the Wallpaper sub-directory and am denied access. I am unable to copy the files to this directory nor can i copy them to another directory. I understand the need for security and to keep people out of files and directories if they have no idea as to what they are doing. This is not my case. I do have some experience with Ubuntu 3 years now and climbing. I do not do anything that may cause my system to have problems without checking first with this forum. 

So to make this long story short---- How do I get access to these directories so that I can add and remove files when I want to?

Thanks for any assistance....

---

### Post by blackbird34 on 2011-12-06
code: 

sudo nautilus

Now you can go anywhere you want! :)

But for wallpaper, you can just open the Appearance preferences, go to the section with the wallpaper thumbnails, and drag 'n' drop. At least i can in my 64 bit Oneiric. No sudo needed ;)

---

### Post by coffeecat on 2011-12-06
@TheTinyt1, for all matters root and sudo, have a look at this community documentation page:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **blackbird34 said:**
> code: 

sudo nautilus

Not a good idea to use sudo with graphical apps. Use gksu or gksudo. See the above link for the reason for this.

---

### Post by TheTinyt1 on 2011-12-06
Ok tried both methods and still no help. 

What I want to do is drag files from the pictures directory to the usr/share/backgrounds directory.

Simple?

Evidently not for me. Didn't have this problem before...

I do agree that sudo -i is much safer than sudo nautilus is. I am not really sure what sudo nautilus does. Kind of scared to use because not sure what it is doing.

---

### Post by Shazaam on 2011-12-06
Try this?....
```
gksudo nautilus
```
Opens nautilus as ROOT with absolute full filesystem permissions so be careful. Leave terminal window open.
Nautilus-Edit-Preferences, tick box to "Show Hidden Files"
Right-click file(s), select "Copy"
Go to target directory(s)/folder(s) and paste into same.
Logout/login to see changes (may not be required, couldn't hurt).

---

### Post by gennatolls on 2011-12-06
Can you not just open system preferences --> Appearance. Then on the left side where the default wallpapers are click the drop down that says "Wallpapers" then select your Pictures folder. Note you can't access subfolders with this method but any pictures in ~/Pictures should show up

---

