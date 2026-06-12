---
title: "Locked file, can not delete"
date: 2009-10-02
forum: General Help
---

### Post by garnold on 2009-10-02
I have a file on my desktop with a lock icon on it. When I try to delete it I get the message that permission is denied. I understand the message but not how to get the proper permission to delete the file. I'm logged in as an admin user so what else is needed? I have uploaded a picture of the file since I'm so new to Ubuntu and this might help better explain my problem. Thank you

---

### Post by bogdan.veringioiu on 2009-10-02
Hi.
I believe the folder is owned by root.

Open a terminal and type
ls -ld ~/Desktop/WmWare*

What do you get?
If if is owned by root, you can delete it by:
sudo rm -fr ~/Desktop/<YourWmwareFolder>
Bogdan

---

### Post by garnold on 2009-10-02
Bingo that did it!
Thank you, guess I have a lot to learn about Ubuntu. Such a learning curve from windows but I just seem so interested in Ubuntu that I want to keep using it an learning more. Thank you again :)

---

### Post by Piccy on 2009-10-02
Consider this to be a feature of Linux over Windows. Where Windows most people log in as administrator and do all sorts of CRAZY things, Linux (Ubuntu) actually has some sort of file permissions at work....

---

### Post by The Cog on 2009-10-02
This might help:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by garnold on 2009-10-02
> **Piccy said:**
> Consider this to be a feature of Linux over Windows. Where Windows most people log in as administrator and do all sorts of CRAZY things, Linux (Ubuntu) actually has some sort of file permissions at work....

I agree with you on this. One of the things I'm liking about Ubuntu is that it makes sure you are doing the right thing. I also really have to say the support from others has been outstanding! The community that supports Ubuntu just seems like a bunch of folks that are really willing to help others. Thank you again!

---

### Post by kanikilu on 2009-10-02
If you don't like having to resort to the terminal, another option is a nautilus plugin called **nautilus-gksu** (in the repos.) which will add a right-click option called "Open as administrator", so you could open your desktop folder (if that's where the folder was that you wanted to delete) with permissions to be able to delete it.

Another useful plugin is nautilus-open-terminal, which will open a terminal in the location that you are in.

Note, logoff and back on for these plugins to take effect (or **sudo pkill nautilus**).

...just my ¢2

---

### Post by garnold on 2009-10-02
> **kanikilu said:**
> If you don't like having to resort to the terminal, another option is a nautilus plugin called **nautilus-gksu** (in the repos.) which will add a right-click option called "Open as administrator", so you could open your desktop folder (if that's where the folder was that you wanted to delete) with permissions to be able to delete it.

Another useful plugin is nautilus-open-terminal, which will open a terminal in the location that you are in.

Note, logoff and back on for these plugins to take effect (or **sudo pkill nautilus**).

...just my ¢2

Excellent! Thank you again.

---

### Post by NeilHoskins on 2009-11-03
> **garnold said:**
> I agree with you on this. One of the things I'm liking about Ubuntu is that it makes sure you are doing the right thing. 

Yes, but come on: having to go to a terminal and remember esoteric commands just to get rid of a protected file?  Surely the graphical file manager (is it called "Nautilus"?) should deal with this in a more user-friendly way.  The chances of mainstream uptake of any Linux distro are absolutely nil while this nonsense continues.

---

### Post by NeilHoskins on 2009-11-03
> **NeilHoskins said:**
> Yes, but come on: having to go to a terminal and remember esoteric commands just to get rid of a protected file?  Surely the graphical file manager (is it called "Nautilus"?) should deal with this in a more user-friendly way.  The chances of mainstream uptake of any Linux distro are absolutely nil while this nonsense continues.

Sorry, I should expand on that statement.  I'm one of the (apparently many) only-semi-clued users who were flummoxed by the Karmic Koala upgrade.  In my case, I had zillions of errors during the upgrade but it seemed to sort itself out with the exception of one package that was supposedly corrupted and won't install.  So I go the the file manager to delete the package in question.  If I try Update Manager, it just tries to install the corrupted package rather than re-download it.  So I conclude that the only course of action is to delete the corrupted package but I run into a brick wall because "permission denied".  At this point I turn to Google and Ubuntu forums, but most people wouldn't bother.

---

### Post by mcduck on 2009-11-03
> **NeilHoskins said:**
> Yes, but come on: having to go to a terminal and remember esoteric commands just to get rid of a protected file?  Surely the graphical file manager (is it called "Nautilus"?) should deal with this in a more user-friendly way.  The chances of mainstream uptake of any Linux distro are absolutely nil while this nonsense continues.

System security sure is not nonsense, and basing the security on use of different user accounts with different permissions (and of course proper authentication when switching between users) seems to be the only really effective way of providing security. That's something that even Microsoft has had to take into account to get rid of the high vulnerability of older Windows releases.

If you don't want to use commands to elevate your privileges, make a launcher for "gksudo nautils". or install the nautilus-gksu package already mentioned.

(Besides, how is the file protected if anybody could just delete it?)

---

