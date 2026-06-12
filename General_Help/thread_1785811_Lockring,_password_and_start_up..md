---
title: "Lockring, password and start up."
date: 2011-06-18
forum: General Help
---

### Post by mawil1013 on 2011-06-18
I've tried to configure ubuntu 10.04.2 to start up without having to enter a password, thought I did all the correct things yet I get this 'lockring' thing where I still have to enter my password every single time I start up. 

I get past the first screen where I was having to enter a password when selecting user, (actually never set up a user, just using whatever the primary 'user' is, what is it called?)

How do I disable the request for a password for this lockring thingy?

Michael A.

Edit: This is the message I get; Unlock Login Keyring

Enter password to unlock your login keyring.

The login keyring did not get unlocked when you logged into your computer.

---

### Post by prodigy_ on 2011-06-18
What is that "lockring" you're talking about and what are you trying to achieve? If you just want auto-login with Gnome, read [this thread](http://ubuntuforums.org/showthread.php?t=1745454).

---

### Post by mawil1013 on 2011-06-18
> **prodigy_ said:**
> What is that "lockring" you're talking about and what are you trying to achieve? If you just want auto-login with Gnome, read [this thread](http://ubuntuforums.org/showthread.php?t=1745454).

This is the full message that ubuntu gives me; 

Unlock Login Keyring

Enter password to unlock your login keyring.

The login keyring did not get unlocked when you logged into your computer.

---

### Post by prodigy_ on 2011-06-18
Try [this HOWTO](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/).

---

### Post by ExileAmongYou on 2011-06-18
You have to open up the "Passwords and Encryption Keys" application (I think it's under System->Administration, and change the password for whichever keyring has your passwords stored in it to a blank one. Having your login password and the keyring password be the same won't work if you're set to automatically login.

---

### Post by mawil1013 on 2011-06-18
> **ExileAmongYou said:**
> You have to open up the "Passwords and Encryption Keys" application (I think it's under System->Administration, and change the password for whichever keyring has your passwords stored in it to a blank one. Having your login password and the keyring password be the same won't work if you're set to automatically login.

On U_10.04.2, I don't see 'Passwords and /or Encryption Keys" in Admin. nor 
Preferences.

---

### Post by mawil1013 on 2011-06-18
> **prodigy_ said:**
> Try [this HOWTO](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/).

Yes, I agree, I'm stupid! I'm just too new to Linux and the english is difficult to understand or as I said, yes, I'm stupid! :lolflag:

It seems it may resolve my issue but I'm going to have to study what they are trying to say. 

It would be nice if someone could post here a summary of the steps he is talking about. But totally don't blame anyone for not having the time.

---

### Post by prodigy_ on 2011-06-18
> **mawil1013 said:**
> On U_10.04.2, I don't see 'Passwords and /or Encryption Keys" in Admin. nor 
Preferences.
Look in the Applications/Accessories menu.

---

### Post by mawil1013 on 2011-06-18
> **prodigy_ said:**
> Look in the Applications/Accessories menu.

I found it, Only 4 items in there, two are obviously for ubuntu forum log in and for my wireless log in, two more have the same title; 'Desktop Couch user authentication and the passwords are very long string of upper and lower case numbers, not sure what to do from here...  :confused:

---

### Post by ExileAmongYou on 2011-06-18
> **mawil1013 said:**
> On U_10.04.2, I don't see 'Passwords and /or Encryption Keys" in Admin. nor 
Preferences.

Oops, sorry, I'm on 11.04 now so I don't have the same menus anymore. It's in Applications->Accessories like prodigy_ said.

---

### Post by mawil1013 on 2011-06-18
> **ExileAmongYou said:**
> Oops, sorry, I'm on 11.04 now so I don't have the same menus anymore. It's in Applications->Accessories like prodigy_ said.

On 10.04.2 it is under Applications > accessories. (Note: see my above reply to you)

---

### Post by ExileAmongYou on 2011-06-18
> **mawil1013 said:**
> I found it, Only 4 items in there, two are obviously for ubuntu forum log in and for my wireless log in, two more have the same title; 'Desktop Couch user authentication and the passwords are very long string of upper and lower case numbers, not sure what to do from here...  :confused:

Right click on the keyring that contains all those passwords and choose Change Password, then set the new password blank. It should have a folder icon and be called something like 'Passwords: default"

---

### Post by mawil1013 on 2011-06-18
> **ExileAmongYou said:**
> Right click on the keyring that contains all those passwords and choose Change Password, then set the new password blank. It should have a folder icon and be called something like 'Passwords: default"

Right click just brings up Properties box and nothing visible that says Change Password.

---

### Post by mawil1013 on 2011-06-18
> **mawil1013 said:**
> Right click just brings up Properties box and nothing visible that says Change Password.

Hold the presses! , I got it, entered old password and left new password blank and it took it, now I'm going to reboot and see what's, what.

---

### Post by mawil1013 on 2011-06-18
> **ExileAmongYou said:**
> Right click on the keyring that contains all those passwords and choose Change Password, then set the new password blank. It should have a folder icon and be called something like 'Passwords: default"

I'm back after reboot and it worked! No more lockring,:popcorn:
thank you!

---

### Post by mawil1013 on 2011-06-18
> **prodigy_ said:**
> Try [this HOWTO](http://karuppuswamy.com/wordpress/2010/06/18/enter-password-to-unlock-your-keyring-prompt-in-ubuntu/).

I now can understand what the website was saying,  thank you for you input!

:popcorn:

---

