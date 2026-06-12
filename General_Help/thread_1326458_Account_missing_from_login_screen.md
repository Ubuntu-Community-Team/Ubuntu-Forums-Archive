---
title: "Account missing from login screen"
date: 2009-11-14
forum: General Help
---

### Post by skippergimp on 2009-11-14
Whilst having various issues palying around with various distros (See [http://ubuntuforums.org/showthread.php?t=1323066](http://ubuntuforums.org/showthread.php?t=1323066)) most things are now fixed.  The odd thing missing is that my user account is missing from the login screen. I have to log in as Other whilst asks for my username.

I find it odd that my account exists but is not displayed as an option.  Where is GDM getting the the account information for this screen?  How do I fix this slight glitch?

---

### Post by tom4everitt on 2009-11-14
I know that one of my accounts were not displayed on the log in screen in Karmic, but that was because I had set the user id manually to 501 (or something like that) to match it with another system. And ubuntu considers all accounts with user id less than 1000 as system users, and will therefore not display them in GDM. 

The command id will give you your user id, but if its not a manually created account it would really suprise me if it had uid below 1000. 

What happens if you activate automatic login? If you delete the account and recreate it?

---

### Post by skippergimp on 2009-11-14
Its the UID.  My account is 500.  I think this is due to a flirtation with with fedora and had the UID changed.  The UID of my wifes account also gave me issues but I managed to fix those.  I will try and sort out my UID then.  Thanks for the pointer.

---

### Post by skippergimp on 2009-11-14
I now have an entry in the login screen (Yeah!!!!). 

I used the following code to do this:

usermod -g xxx -u xxx username

where xxx are numbers over 1000.  Whilst reading this thread ([http://ubuntuforums.org/showthread.php?t=405268](http://ubuntuforums.org/showthread.php?t=405268)) to change my UID, I thought I had better run sudo chown -R <user>:<user> /home/<user> to make sure all my files belong to me. When I run it I get "chown: cannot access `/home/dapo/.gvfs': Permission denied" Looking at the properties of the folder, it appears as mine in user and group sense.  Why would i be getting this error?  Could I safely sudo rm it?

---

### Post by skippergimp on 2009-11-14
.gvfs does appear empty......

---

### Post by skippergimp on 2009-11-14
No worries, tried it again and it worked without any errors!

---

