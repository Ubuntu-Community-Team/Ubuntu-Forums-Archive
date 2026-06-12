---
title: "Desktop Backgrounds"
date: 2012-04-29
forum: General Help
---

### Post by AlanR8 on 2012-04-29
So, 12.04, happy since Alpha 1 BTW. 

However have not found a solution for this issue. If I select an "Ubuntu" desktop wallpaper, it will be applied during the login process. Cool. 

I use wallpapers from my Pictures folder and they will NOT form part of the login process.

So I moved some pictures to the folder:

usr\share\backgrounds

where the official Ubuntu pics are and it still won't use my choice during the login process.

Am I missing something?

---

### Post by hal8000 on 2012-04-29
> **AlanR8 said:**
> So, 12.04, happy since Alpha 1 BTW. 

However have not found a solution for this issue. If I select an "Ubuntu" desktop wallpaper, it will be applied during the login process. Cool. 

I use wallpapers from my Pictures folder and they will NOT form part of the login process.

So I moved some pictures to the folder:

usr\share\backgrounds

where the official Ubuntu pics are and it still won't use my choice during the login process.

Am I missing something?



I just tried this on my newly installed Ubuntu 12.04.
When I copy any images to /usr/share/backgrounds  (/ correct way around)
they do not appear in the list of wallpaper.

I opened a terminal and checked permissions and they are all the same
chmod 644 and owned by root.

Now here is what worked for me.
Right click and change the background, and click the + sign. Then navigate to /usr/share/backgrounds and highlight the image and click open.

For me this sets the background the same in Gnome (I'm using gnome classic) and also the Light DM display screen.

---

### Post by AlanR8 on 2012-05-01
Thanks for that, worked a treat!

---

### Post by Steven D on 2012-05-03
I actually just had this issue and skimmed the forums to see if anyone was wondering...
My login screen had paused, had to do a hard reset. Log had informed me that system had stopped due to "incorrect permission, XYZ wallpaper.png" turns out my wallpapers folder was set to No "group" access, but the "others" group also had no read access. I changed it so all others users and groups could read the files, and selected "Apply Permissions to Enclosed Files" This allowed me to use my own wallpapers folder images in the login screen, and solved my periodic "loggin in" error hang.

PS: wallpapers folder copied from my NTFS drive also set the permission to no read from others or group. maybe it's something I'm doing on my windows box that mucks up the permissions?

---

