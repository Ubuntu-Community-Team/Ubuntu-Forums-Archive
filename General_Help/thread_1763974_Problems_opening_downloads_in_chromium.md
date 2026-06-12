---
title: "Problems opening downloads in chromium"
date: 2011-05-21
forum: General Help
---

### Post by jezzyjez on 2011-05-21
Upon downloading a file and clicking to open an error occurs.

```
Could not display "/home/jez/Downloads/first2007.pdf".

The location is not a folder.
```

I then open my downloads folder in nautilus and can open the file correctly.

It is not only pdf file which i have this problem with.

Please help 
Jez

---

### Post by 3xp10r3r|X13 on 2011-05-21
This will happen to all files which aren't folders, so you just do a right click and select "open containing folder".
--> It's probably just chrome, why don't you just use another browser?

---

### Post by jezzyjez on 2011-05-21
> **3xp10r3r|X13 said:**
> This will happen to all files which aren't folders, so you just do a right click and select containing folder.
--> It's probably just chrome, why don't you just use another browser?

I'm pretty sure it's not down to chromium as this function worked perfectly before I upgraded to Natty.

---

### Post by 3xp10r3r|X13 on 2011-05-21
fair enough, I'll try it out my self and hopefully I'll manage to establish a solution.

---

### Post by teachop on 2011-05-21
Are you using Unity?

---

### Post by bdoe on 2011-05-21
It's not a Chromium problem, as it works just fine for me. It's also not likely a Natty problem, as it would also affect me running Mint 11.

Check your preference settings in Chromium (click the wrench icon and select "Preferences"). Click on "Under the Hood" and verify the proper download path is set. Check letter case, as Linux is case-sensitive (if you have it set to look for /home/user/Downloads, and the actual path is /home/User/Downloads, it will fail). Finally, make sure your Downloads folder is executable (open a terminal and type "ls -l ~/", without the quotes, and check that the permissions for Downloads is "drwxr-xr-x" or "drwx------"). If all else fails, then make a backup of your bookmarks, and completely reset Chromium's settings by deleting ~/.config/chromium, which Chromium will rebuild with default settings on next launch.

---

### Post by 3xp10r3r|X13 on 2011-05-21
Just tried it out and it works fine (if it has something to do with your desktop environment - according to teachop's post - I'm using KDE)

But I still don't get why you're using chrome in the first place. 

Use firefox:
[http://www.mozilla.com]("http://www.mozilla.com/en-US/firefox/fx/")

OR

Use opera:
[www.opera.com]("http://www.opera.com")

There are fast, relieable and offer a lot of extra functions (referring to the firefox add ons)

---

### Post by teachop on 2011-05-21
A thread to read if you are using Unity and have touched XFCE or Thunar:
[http://ubuntuforums.org/showthread.php?t=1729680]("http://ubuntuforums.org/showthread.php?t=1729680")

---

### Post by jezzyjez on 2011-05-21
> **bdoe said:**
> It's not a Chromium problem, as it works just fine for me. It's also not likely a Natty problem, as it would also affect me running Mint 11.

Check your preference settings in Chromium (click the wrench icon and select "Preferences"). Click on "Under the Hood" and verify the proper download path is set. Check letter case, as Linux is case-sensitive (if you have it set to look for /home/user/Downloads, and the actual path is /home/User/Downloads, it will fail). Finally, make sure your Downloads folder is executable (open a terminal and type "ls -l ~/", without the quotes, and check that the permissions for Downloads is "drwxr-xr-x" or "drwx------"). If all else fails, then make a backup of your bookmarks, and completely reset Chromium's settings by deleting ~/.config/chromium, which Chromium will rebuild with default settings on next launch.


The preferances are correct as the files do save to the downloads folder, the permissions for the folder is drwxr-xr-x and I have already done a removal and reinstall of chromium to try an solve this problem before

---

### Post by jezzyjez on 2011-05-21
> **teachop said:**
> Are you using Unity?


No I'm using GNOME

---

### Post by teachop on 2011-05-21
> **jezzyjez said:**
> No I'm using GNOME
Ok.  I had this same problem, and it was caused by installing Xubuntu-destop (=XFCE, =Thunar) on top of Ubuntu back when I was not acclimated to Unity yet.  Thunar brings in a package that causes this exact problem, you can read the link I posted above.

---

### Post by bdoe on 2011-05-21
> **jezzyjez said:**
> The preferances are correct as the files do save to the downloads folder, the permissions for the folder is drwxr-xr-x and I have already done a removal and reinstall of chromium to try an solve this problem beforeI don't believe removal of Chromium through Synaptic, Software Manager, or apt automatically removes the config folder. It might be worth verifying this though.

---

