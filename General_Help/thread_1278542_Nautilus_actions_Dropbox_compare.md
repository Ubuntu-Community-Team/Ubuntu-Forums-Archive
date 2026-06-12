---
title: "Nautilus actions Dropbox compare"
date: 2009-09-29
forum: General Help
---

### Post by Fl0ris on 2009-09-29
Hi all :)

I'd like to have an Addon for the file storage service Dropbox, but I've not much experience with Nautilus Actions.

Could anyone help me with creating a Nautilus actions script (Ubuntu) which is executable on *every* file and does the following (in chronologic order)
1) Checks if there exists a version of the file you clicked on, with the same name + ~ symbol. 
E.g. you execute the Nautilus actions script on a file called **/home/yourname/test.txt** and the script verifies if there exists a file named **/home/yourname/test.txt~**
2) - If yes, it executes the following action (I prefer not in the terminal):
**kompare [name of the file you clicked on] [name of the file you clicked on + ~]**
An example:
**kompare /home/yourname/Desktop/test.txt /home/yourname/Desktop/test.txt~**
- If no, it does nothing. Eventually an alert or prompt with: 
"No older revision of this file found."

Excuse me for grammatical errors, I have typed this post quite quickly.

You can export the Nautilus Actions config files and post it here at the forums.

(Many) thanks in advance for your support!

BTW, if you sign up to Dropbox via [my referral link]("https://www.getdropbox.com/referrals/NTE4NjE5MDY5") you'll get 250 MB free extra space.

---

### Post by Fl0ris on 2009-09-29
Although it took some time, I managed to create it myself (I think I was just too impatient).

Config file is located here: 

[http://dl.getdropbox.com/u/1861906/Nautilus_actions_dropbox_config.schemas](http://dl.getdropbox.com/u/1861906/Nautilus_actions_dropbox_config.schemas)

---

