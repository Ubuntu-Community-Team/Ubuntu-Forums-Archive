---
title: "Frustrated"
date: 2012-06-10
forum: General Help
---

### Post by ktook on 2012-06-10
Have a laptop (500gb) dual boot with Win 7 Pro, and Ubuntu 12.04 early initial version installed.  I recently downloaded and burned to dvd the most recent version of 12.04.  I thought that when I installed the latest version it would essentially overlay the previous version.  No, that did not happen,  no doubt my fault, but I do not know where.  Now, I would like to get back to ground zero, and start over with the dual boot of windows and using the latest version of Ubuntu.  Where do I start without loosing Win 7?  I love Ubuntu and will with no doubt be soon a single Linux system user.   Thanks, ken

---

### Post by wilee-nilee on 2012-06-10
> **ktook said:**
> Have a laptop (500gb) dual boot with Win 7 Pro, and Ubuntu 12.04 early initial version installed.  I recently downloaded and burned to dvd the most recent version of 12.04.  I thought that when I installed the latest version it would essentially overlay the previous version.  No, that did not happen,  no doubt my fault, but I do not know where.  Now, I would like to get back to ground zero, and start over with the dual boot of windows and using the latest version of Ubuntu.  Where do I start without loosing Win 7?  I love Ubuntu and will with no doubt be soon a single Linux system user.   Thanks, ken

Post a screen shot of gparted and identify what you want and what you don't want.

You may have to install gparted, so install it in the one you want to keep and take the screenshot there, if you can't identify the partitions.

---

### Post by drs305 on 2012-06-10
If you downloaded the 12.04 official release from the Ubuntu web site you should have the most up-to-date version. The 12.04.1 update will be releases in August I believe.

If you install the DVD to a dedicated partition, using the "Something Else" option and select a dedicated partition, and choose to format the partition it should install a clean version of 12.04. I'm not sure what you did differently the first time, unless you chose not to format the partition.

---

### Post by black veils on 2012-06-10
not quite sure what you mean *did*  happen. boot the ubuntu live cd, choose **try** to load the desktop environment. open **gparted** and take a screenshot of it. post it here (attach image using the paperclip), so we can see what state the harddrive is in.

---

### Post by ktook on 2012-06-10
> **drs305 said:**
> If you downloaded the 12.04 official release from the Ubuntu web site you should have the most up-to-date version. The 12.04.1 update will be releases in August I believe.

If you install the DVD to a dedicated partition, using the "Something Else" option and select a dedicated partition, and choose to format the partition it should install a clean version of 12.04. I'm not sure what you did differently the first time, unless you chose not to format the partition.

I am not sure now just what I did during this update.  But, there are two versions of Ubuntu 12.04 out there with multiple pointers in the Grub.  I would like to clean it up to only have Win 7 and one version of Ubuntu.  (honestly, I am getin old (81))...  And willing to learn.  Thanks..

---

### Post by drs305 on 2012-06-10
> **ktook said:**
> I am not sure now just what I did during this update.  But, there are two versions of Ubuntu 12.04 out there with multiple pointers in the Grub.  I would like to clean it up to only have Win 7 and one version of Ubuntu.  (honestly, I am getin old (81))...  And willing to learn.  Thanks..

Ah, this is not what I was imagining.  ;-)

So your Ubuntu is working? No need to reinstall anything in that case. But for us to get a clearer picture of what is happening, it might be best for you to run the boot info script and post the contents or link to RESULTS.txt. 

You can do it from Boot Repair, which you can install with instructions in the link in my signature line.

The second entry isn't marked "Recovery" is it? That would be a normal installation. If the second "Ubuntu" is hidden in a subdirectory called "Previous Linux versions" that is also normal.

---

### Post by ktook on 2012-06-10
> **drs305 said:**
> Ah, this is not what I was imagining.  ;-)

So your Ubuntu is working? No need to reinstall anything in that case. But for us to get a clearer picture of what is happening, it might be best for you to run the boot info script and post the contents or link to RESULTS.txt. 

You can do it from Boot Repair, which you can install with instructions in the link in my signature line.

The second entry isn't marked "Recovery" is it? That would be a normal installation. If the second "Ubuntu" is hidden in a subdirectory called "Previous Linux versions" that is also normal.

OK, I have on my screen the GParted info, now, how do I take a picture of it to show you?    Hey, I am learning ( or perhaps re-learning), never too old, is it?

---

### Post by ktook on 2012-06-10
> **drs305 said:**
> Ah, this is not what I was imagining.  ;-)

So your Ubuntu is working? No need to reinstall anything in that case. But for us to get a clearer picture of what is happening, it might be best for you to run the boot info script and post the contents or link to RESULTS.txt. 

You can do it from Boot Repair, which you can install with instructions in the link in my signature line.

The second entry isn't marked "Recovery" is it? That would be a normal installation. If the second "Ubuntu" is hidden in a subdirectory called "Previous Linux versions" that is also normal.

"The second entry isn't marked "Recovery" is it? That would be a normal  installation. If the second "Ubuntu" is hidden in a subdirectory called  "Previous Linux versions" that is also normal."  The answer is yes...

---

### Post by drs305 on 2012-06-10
> **ktook said:**
> OK, I have on my screen the GParted info, now, how do I take a picture of it to show you?    Hey, I am learning ( or perhaps re-learning), never too old, is it?

The PrtSc key should probably do it; otherwise click DASH (top left), start typing "Screenshot" and when "Screenshot" is the first icon in the opening pane hit ENTER to activate it.

The boot info script will give us a much better idea of what is going on with your system, however.

---

### Post by black veils on 2012-06-10
> **ktook said:**
> OK, I have on my screen the GParted info, now, how do I take a picture of it to show you?    Hey, I am learning ( or perhaps re-learning), never too old, is it?


at the top-right of the keyboard, above the **Backspace** key, there is a key with PrtSc on, press it and the screenshot app should show, follow the instructions. once the image is saved, create a reply message to this thread, attaching the image with the paperclip.

---

### Post by ktook on 2012-06-10
> **black veils said:**
> at the top-right of the keyboard, above the **Backspace** key, there is a key with PrtSc on, press it and the screenshot app should show, follow the instructions. once the image is saved, create a reply message to this thread, attaching the image with the paperclip.

Ok, I got the picture, now how do I attach it to the note, I see mentioned "paperclip", where do I get that?    (oh, I feel so stupid at times)

I found "Manage Attachments" and did an upload.  Where did it upload it to?   And, will you see it?  Yikes

---

### Post by ktook on 2012-06-10
> **drs305 said:**
> The PrtSc key should probably do it; otherwise click DASH (top left), start typing "Screenshot" and when "Screenshot" is the first icon in the opening pane hit ENTER to activate it.

The boot info script will give us a much better idea of what is going on with your system, however.

Say, I have received a lot of info from you and others.  I just want to say thanks to all.   I maybe  back sometime toward the end of the week as we are traveling about 1700 miles north to our NY home.  I probably will not be on for the next few days.  Again really appreciate yours and everyone's help.   ;)  Ken  (I learned a lot)

---

