---
title: "Could not update ICEauthority error on logon"
date: 2009-12-12
forum: General Help
---

### Post by BenW on 2009-12-12
Hello,

I have a small problem (I hope). I just got Ubuntu for my laptop (a Dell Inspiron E1505, installed it, installed wifi drivers, and the applications that I wanted from the Applications/Ubuntu software Center. Also Halo 1 (the pc game) and Wolfenstein Enemy Territory.

Now here is my problem. After I installed everything I restarted my computer and had the following error pop up just after I logged in but before the desktop panels and background loaded. 
```
could not update ICEauthority file /home/ben/.ICEauthority
```Naturally after seeing could not update I ran the Update Manager from System/Administration and my system is of course is "... up-to-date"

So, my question is how did this happen (because I am naturally curious) and how do I fix it?

(by the way, I am new to Linux so sorry if this is a foolish question and sorry if I used the wrong prefix)

---

### Post by rbc on 2009-12-12
It is not a question of .ICEauthority being the latest version. There was probably more to that error, specifically that you (your user profile) no longer had rights to use that file. Open terminal and try these two consecutive commands:

sudo chown ben:ben /home/ben/.ICEauthority 
sudo chmod 600 /home/ben/.ICEauthority

---

### Post by oldos2er on 2009-12-12
Not a foolish question at all. Something (difficult to say what) has changed the permissions of .ICEauthority, so you need to change them back. Open a terminal and run these commands one at a time:```
sudo chown /home/BenW/.ICEauthority
sudo chmod 644 /home/BenW/.ICEauthority
```
assuming your username is 'BenW'.

---

### Post by BenW on 2009-12-13
It worked perfectly! :D Thanks a lot guys ;)

---

### Post by IanVaughan on 2010-03-23
[None of this worked for me!?]("http://ubuntuforums.org/showthread.php?p=9016355")

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

