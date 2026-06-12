---
title: "Firefox/Thunderbird Slow menus"
date: 2011-08-21
forum: General Help
---

### Post by mbnickson on 2011-08-21
I am a new user to Ubuntu and so far absolutely love it. The one problem i'm having is that while using Firefox and Thunderbird, the menus have a lag when being clicked of about 30-40 seconds before they open.  

I've had a quick look on other forums and someone suggested downloading Firefox and Thunderbird from the Mozilla website. I gave this a try but then when i tried opening Thunderbird i got an error message saying the tar.bz2 file was corrupt. 

I have uninstalled Thunderbird and Firefox because they are just too slow but i can't find a suitable email client for my business email so really need to find a solution to the lagging menus in Thunderbird.

Can anyone offer some suggestions but bear in mind i'm not used to the terminal or adding long lines of code.

Thanks for any help.
Michael

---

### Post by magic8ball on 2011-08-21
I installed the latest stable Firefox and Thunderbird (both version 6) by adding the PPA repositories as described in the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

The first set of commands in the first post will upgrade your Firefox to the latest stable release.  If you substitute Thunderbird for Firefox in the first and fourth lines, you can also use these commands to upgrade to the latest stable Thunderbird.

Good Luck.

---

### Post by mbnickson on 2011-08-23
Thanks for your reply.
 
I gave the cammands a try but they didn't work. All that happened was that I got a folder appear in the Software Centre labelled "Thunderbird Stabel Release" which had various releases of Thunderbird with various languages supported.
 
I tried installing one which appeared to as if it could be the correct file for me, but the file would not install.
 
Back to the drawing board i think.......

---

### Post by lovinglinux on 2011-08-24
Sounds like a video driver issue to me. Make sure you have the latest driver for your video card installed.

---

### Post by mbnickson on 2011-08-30
Just incase this helps anyone for future reference.
 
I solved my issue with slow menus purely by luck more than anything.  I removed my email account from Thunderbird and then manually set up the email account username/port settings. This seems to have fixed the slow menus and my email works fine.  I am using a POP3 server for my business email.

---

