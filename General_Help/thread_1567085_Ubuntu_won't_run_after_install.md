---
title: "Ubuntu won't run after install"
date: 2010-09-03
forum: General Help
---

### Post by bkdamon on 2010-09-03
Hello all,
 
I'm curious about Ubuntu and tried to install the latest 32 bit version (386) on a Compaq Presario (P4, 1G ddr) and it seemed to go well but when it finishes I can see the desktop and a few icons but when I moved the mouse the screen went black. Used the live cd and got the same thing.
 
I'd like to give Ubuntu a fair chance before giving up on it so I was wondering what direction you would suggest I take?
 
I build computers now and then and tinker with them for friends and family. I've installed and reinstalled windows countless times but I'm not really up on a lot of the jargon about compiling and stuff and I have no experiance with linux but I was fairly capable with dos back in the day (writing bat files and such). I just add this so you'll know my level of understanding (low). :D
Thanks for reading!

---

### Post by sikander3786 on 2010-09-03
Welcome to the forums.

Did you mean using the Live CD (only the 2nd time) caused the screen to go black on mouse movements as you successfully installed Ubuntu at first?

---

### Post by Rubi1200 on 2010-09-03
What graphics card do you have installed for your version?

---

### Post by gypsumwolf on 2010-09-03
I had a weird thing happen that may be similar to yours or not at all.
I did a fresh install of Xubuntu and when the computer booted up and I went to move the mouse,the computer went straight into the screen-saver which can be a black screen. I move the mouse for a short time then I would get out of the screen-saver. It was weird, like a immediate screen-saver.

But, your issue is still most likely it is a graphics card issue.

---

### Post by bkdamon on 2010-09-03
.

---

### Post by bkdamon on 2010-09-03
> **sikander3786 said:**
> Welcome to the forums.
 
Did you mean using the Live CD (only the 2nd time) caused the screen to go black on mouse movements as you successfully installed Ubuntu at first?
 
I did try the live cd a few times and also followed up with a full install to a formatted HD a couple times but I get the same results.

---

### Post by bkdamon on 2010-09-03
> **Rubi1200 said:**
> What graphics card do you have installed for your version?
 
> **gypsumwolf said:**
>  
But, your issue is still most likely it is a graphics card issue.
 
The MB has onboard intel extreme (not) graphics.

---

### Post by Rubi1200 on 2010-09-03
Try restarting the computer with the LiveCD and then boot using the following parameter: i915.modeset=1

See here for instructions:
[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

If it works then you know what the issue is and we can take it from there.

---

### Post by bkdamon on 2010-09-03
Will do. Thanks! I'll get back to you once I try that with the results.

---

