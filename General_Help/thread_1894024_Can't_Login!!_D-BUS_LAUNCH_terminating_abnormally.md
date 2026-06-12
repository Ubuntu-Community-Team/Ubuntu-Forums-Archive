---
title: "Can't Login!! D-BUS LAUNCH terminating abnormally"
date: 2011-12-11
forum: General Help
---

### Post by mxndrwgrdnr on 2011-12-11
Came out of nowhere. I believe it happened after I left my laptop out  and on and the battery died. After plugging it in and logging on I get  "Could not connect to  session bus: //bin/dbus-launch terminated  abnormally without any error". can't make any sense of it and i can't  log onto my own desktop! can't access my files!
need help!
thanks

---

### Post by Cookieh on 2011-12-11
Try to log in to your root account if you have a password set, if not, try to do a recovery or file backup with another computer/ laptop

---

### Post by mxndrwgrdnr on 2011-12-11
is that done by logging in as "other" user in the login selection screen?

---

### Post by mxndrwgrdnr on 2011-12-11
and any idea what happened or why this is happening? or also how to unmark this thread from solved?

---

### Post by Cookieh on 2011-12-11
yeah its done by loging in wwith other... Also this might be a problem with Pytthon as D-BUS is to do with Python, as far as I know it, something must have altered or deleted some python libraries, I just recently switched to Ubuntu and from my error experience I got some really hard errors such as getting out of Grub Rescue, but I have never seen something to do with D-BUS LAUNCH... I would suggest you to either check anything about it in [https://help.ubuntu.com/](https://help.ubuntu.com/) or just by typing all the details up in google...

---

### Post by Cookieh on 2011-12-11
Sorry but I think I cant help you...

---

### Post by Cookieh on 2011-12-11
BTW have you got to log in with root, or you cant access the whole log in screen... More detail plz..

---

### Post by Cookieh on 2011-12-11
[FONT=Arial Black]One more thing... Try to go into a recovery mode.... To go into recovery mode, 
[/FONT]
[LIST=1]
[*][FONT=Arial Black]Switch on your computer [/FONT]
[*][FONT=Arial Black]Wait until the BIOS finishes loading (you will probably see a logo of your computer manufacturer) [/FONT]
[*][FONT=Arial Black]The following messages will show up:[/FONT]
[FONT=Arial Black]Grub loading stage1.5  Grub loading, please wait...  Press ESC to enter the menu[/FONT][FONT=Arial Black][/FONT]
[*][FONT=Arial Black]Quickly press the Escape key, which will bring up a boot menu.  (If you see the Ubuntu logo, you've  [/FONT]
[*][FONT=Arial Black]Select the line ending with '(recovery mode)', probably the second line, something like: [/FONT]
[FONT=Arial Black]Ubuntu, kernel 2.6.17-10-generic (recovery mode)[/FONT][FONT=Arial Black][/FONT]
[*][FONT=Arial Black]Press enter and your machine will begin the boot process. [/FONT]
[*][FONT=Arial Black]After  a few moments, your workstation should display a menu with a number of  options.  One of the options (you may need to scroll down to the bottom  of the list) will be "Drop to root shell prompt".   [/FONT]
[/LIST]
[FONT=Arial Black]**NOTE:**  Users of Ubuntu Karmic (9.10) and higher will need to press and hold  the left Shift key instead of Escape in step 4, and may not see the  "Grub loading, please wait..." message in step 3. [/FONT]

---

### Post by mxndrwgrdnr on 2011-12-11
not sure i understand how to log in as root...I can access the login screen, just don't know what username to use as "Other". are you suggesting that there is no hope for recovering my system at this point and that now its just a matter of saving my files? there doesn't seem to be any help related to my issue anywhere else.

---

### Post by Cookieh on 2011-12-12
You could just backup your files on to another Ubuntu install. But try to login as root by username : root
     password : Your Set Password
 
But I would suggest to get all your files backed up somehow, either connect hard drive to another computer, or by going into GRUB menu by the way above...

---

