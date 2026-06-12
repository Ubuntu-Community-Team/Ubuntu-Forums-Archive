---
title: "Problem with installation on ASUS P7P55D PRO"
date: 2011-09-21
forum: General Help
---

### Post by at2766 on 2011-09-21
I built a computer within the last year and i have a **ASUS P7P55D PRO** mother board with an **INTEL CORE i5** (first gen) processor. when i  try to install Ubuntu it look like its attempting to boot, but when loading i get a black screen with a flashing white underscore in the top left of my screen. I have no idea how to fix this issue. 
 
Please email me at <snip> if you have any ideas, it will be much appriciated.

---

### Post by Mark Phelps on 2011-09-21
Couple of side comments on your post ...

First of all, BAD idea to include your email.  Good way to get spam bott'ed.

Second, forums are for SHARING problems and solutions -- so others with the same problems can find solutions that work.  Using email to do this defeats the very purpose of the forums.

---

### Post by josephmills on 2011-09-21
I 100% agree that you should never put you email up. 

but after that what is your VGA ? 

open terminal and type in ```
lspci -nn | grep VGA 
```and paste that here.

---

### Post by Slim Odds on 2011-09-21
> **Mark Phelps said:**
> Couple of side comments on your post ...

First of all, BAD idea to include your email.  Good way to get spam bott'ed.

Second, forums are for SHARING problems and solutions -- so others with the same problems can find solutions that work.  Using email to do this defeats the very purpose of the forums.

At least the subject was very helpful.... :(

---

### Post by drs305 on 2011-09-21
You most likely have a video problem.

Start the computer, hold down the SHIFT key, and wait for the Grub 2 menu to appear. 

Highlight the first entry and press 'e' to enter the editing mode.

Go to the end of the 'linux' line and remove 'quiet splash' and add 'nomodeset'.

Press CTRL-x to boot.

If it now boots, open the Additional Drivers app (how depends on your version) and try to add your video card.

**As a moderator:** Please remove the email address. It's not a good idea to have it in the open as others have suggestions. Users can post their responses here. There is an option to forward notifications to your email address or to email you via your UF page if desired. You can get to it via the User CP link at the top right of the page, then go to Edit Options.

---

### Post by at2766 on 2011-09-27
> **drs305 said:**
> You most likely have a video problem.
 
Start the computer, hold down the SHIFT key, and wait for the Grub 2 menu to appear. 
 
Highlight the first entry and press 'e' to enter the editing mode.
 
Go to the end of the 'linux' line and remove 'quiet splash' and add 'nomodeset'.
 
Press CTRL-x to boot.
 
If it now boots, open the Additional Drivers app (how depends on your version) and try to add your video card.
 
**As a moderator:** Please remove the email address. It's not a good idea to have it in the open as others have suggestions. Users can post their responses here. There is an option to forward notifications to your email address or to email you via your UF page if desired. You can get to it via the User CP link at the top right of the page, then go to Edit Options.
 
so i tried this and i delete the quiet splash but there was no nomodeset to delete and when i hit CTRL-x i still just get that little flashing '_' in the corner

---

### Post by drs305 on 2011-09-27
> **at2766 said:**
> so i tried this and i delete the quiet splash but there was no nomodeset to delete and when i hit CTRL-x i still just get that little flashing '_' in the corner

After deleting the *quiet splash* you would then **add** *nomodeset* by typing it in. Then press CTRL-x.

You will see when you edit the menuentry on the next boot that you will have to repeat this process, as these changes are not saved. If it boots to the Desktop and you can add a video driver, this change should not be required any longer. If you can't add a driver but nomodeset works, we can make it permanent by editing some of the Grub files.

---

