---
title: "A total mess - LightDM, Unity, everything"
date: 2011-10-17
forum: General Help
---

### Post by omeromer on 2011-10-17
Well after a few days of trying to fix this by myself and just causing more problems I come here.

This is what happened:

A while back, I broke my unity with the compiz configuration, I did just about everything to fix it and I failed.

I switched to gnome classic for a few month and when I got sick of it (about a week ago) I decided to try again and fix it now that I'm more experienced with Linux and Ubuntu and I tried this:
Creating a new user to see if unity and compiz will work, and if they will I will copy all the config file to my original user.

I tried it, created the new user, unity worked, I copied the config file from the new user to the original user, and it worked great and I ran unity just fine for a few days.

Now this is where the problems began:
Since I knew unity was going to get updated in a few days (it was like 2 days before the 11.10 release) I decided to try and mess again with the compiz configuration, since I thought the update will fix it anyway.

It took 2 clicks of a button to break compiz and unity all over again, but this time the replacing of the config files from the new users didn't fix it.

The update for 11.10 came out, I started updating and while the upgrade was downloading new packages the power cable of my PC was disconnected by mistake, which turned it off, I turned the PC back on and resumed the update, the update finished, installed everything, the PC restarted and Ubuntu started.

The new login screen was there, which made me think everything went fine even though the incident with the power, but when I tried to log in on my regular user, it started running commands (like a full-screen terminal), and after a second it just put me back right in the login screen.

I tried logging in with the user I made in order to fix compiz and unity, and this user worked just fine, I gave it sudoer and admin privileges, and started trying to work out what was the problem.

For some reason, nautilus was completely broken, every time I tried to open a folder there was a 50% change nautilus will crash, so I had to do everything from terminal (just until I found out there are other file browsers out there).

In any way, after googling a little about login problems similar to mine, In some forum I saw someone say to run this command:

```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```After I ran this command I had a 2 option screen, The first option (I think): GDM, the second option: "LightDM"

I tried choosing LightDM, logging out of the user and trying to log in with the original one, and it still didn't work.

I ran the command again this time choosing GDM, and still it didn't work.

I restarted my PC and now ubuntu is just stuck at the 

Ubuntu
- - - - - - 

screen...


I don't think I can go on from here anymore - I REALLY need help - I am writing this from a 11.10 Live CD.

Thanks for reading this far, just wanted to make sure I mention everything that has happened.

Tell me if you need any extra information.

---

### Post by flipper T on 2011-10-17
reinstall ?

should take you 15 minutes.

---

### Post by omeromer on 2011-10-17
Wouldn't that erase everything?

---

### Post by flipper T on 2011-10-17
thats why we back up...

---

### Post by omeromer on 2011-10-17
Well I don't backup - I need a different solution.
Reinstalling is a solution for everything, but it's just like telling someone to kill himself to cure a disease.

---

### Post by philinux on 2011-10-17
Since the upgrade was interupted does updating cause any errors.

You could try this in a terminal.

sudo dpkg --configure -a

---

### Post by omeromer on 2011-10-17
I managed to get the login screen back by ctrl+alt+f1 while ubuntu was in the screen I said I was stuck in, ran the command that broke it, picked lightdm and now it's working, but I still can't log in as the original user.

phil, I ran your command and it did nothing (it gave no output, no idea if it did anything)

---

### Post by ajgreeny on 2011-10-17
Even if you haven't backed up (yet) you can still do so now with the live CD by opening nautilus with root permissions ```
gksu nautilis
```and then copying all your /home/user files to an external disk or disks of some sort, CD, DVD, flash drive, hard drive, take your choice.  Having done that, reinstall, then copy back your backed up home files.

There is no point saying "Well I don't backup - I need a different solution" if all that we have suggested does not work for you.

What would you do if your hard disk suddenly died;  it can happen, and always at the very worst moment, ie, when you have no backup of anything.

---

### Post by omeromer on 2011-10-17
Yes I know now that I need to backup - this I will do but if I just copy all the user files back the problem will resume - since the problem only happens with 1 user - my main user

---

### Post by philinux on 2011-10-17
> **omeromer said:**
> I managed to get the login screen back by ctrl+alt+f1 while ubuntu was in the screen I said I was stuck in, ran the command that broke it, picked lightdm and now it's working, but I still can't log in as the original user.

phil, I ran your command and it did nothing (it gave no output, no idea if it did anything)

That means all the packages are correctly configured. 
I treat re-installing as a last resort. But I have a feeling that is your best bet.

---

### Post by omeromer on 2011-10-17
> **philinux said:**
> That means all the packages are correctly configured. 
I treat re-installing as a last resort. But I have a feeling that is your best bet.
Isn't there anyway to try and debug to see what causes the users to not be able to log in?
Since 1 user does work.

---

### Post by philinux on 2011-10-17
> **omeromer said:**
> Isn't there anyway to try and debug to see what causes the users to not be able to log in?
Since 1 user does work.

From what you describe in your first post it sounds like a very bad upgrade. You could spend hours or worse longer trying to fix it. Someone else may have a solution.

I would backup import stuff in any case.

I'm about to upgrade mine as a test. I have home on its own partition. I've usually had bad results upgrading and usually end up re-installing.

---

### Post by omeromer on 2011-10-17
I know I sound like a broken record but I just don't think it can be that bad if 1 of the users still works perfectly fine.

I just need to at-least try to debug what causing it to go back to the login screen on some of the users when I try to log in...

Just to describe what's happening again:

When I try to log in on my main user, it shows a black screen doing commands (I believe it's starting services, with the [OK]'s on the right of the screen), and when it reaches "Checking battery state" (or something similar) it just goes back to the login screen like nothing happened.

I tried taking a picture with my phone to read what it says, if you want I can post it, but it sometimes says different stuff so I don't think they have anything to do with what's causing it.

I really want to avoid reinstalling.

---

### Post by philinux on 2011-10-17
> **omeromer said:**
> I know I sound like a broken record but I just don't think it can be that bad if 1 of the users still works perfectly fine.

I just need to at-least try to debug what causing it to go back to the login screen on some of the users when I try to log in...

Just to describe what's happening again:

When I try to log in on my main user, it shows a black screen doing commands (I believe it's starting services, with the [OK]'s on the right of the screen), and when it reaches "Checking battery state" (or something similar) it just goes back to the login screen like nothing happened.

I tried taking a picture with my phone to read what it says, if you want I can post it, but it sometimes says different stuff so I don't think they have anything to do with what's causing it.

I really want to avoid reinstalling.

Like I said last resort. Your new info.
Try this when it hangs.
 [http://techspear.com/2011/08/booting-ubuntu-oneiric-stops-at-checking-battery-state-ok/](http://techspear.com/2011/08/booting-ubuntu-oneiric-stops-at-checking-battery-state-ok/)

---

