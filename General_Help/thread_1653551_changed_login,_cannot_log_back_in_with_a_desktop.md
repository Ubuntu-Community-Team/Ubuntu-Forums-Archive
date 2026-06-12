---
title: "changed login, cannot log back in with a desktop"
date: 2010-12-27
forum: General Help
---

### Post by deadpieface on 2010-12-27
First of all thanks for your time.

System>admin>users... I changed my login name from X to Y.

After a system restart, I selected Y and logged in. Desktop is completely gone. Says that I need to change a folders name to something else...basically I think I screwed up so my home folder is not accessable via the changed login name. I did not realize that would interfere. When I use ctrl alt f1 I get X@computer instead of Y@computer. Not sure what appropriate steps are now.

I can find my /X home but it is encrypted.

At work on my EVO sorry for crappy indication of error message.

---

### Post by deadpieface on 2010-12-27
okay back at home and after booting and selecting Y as login:
 
"Could not update ICEauthority file /home/ryan/.ICEauthority"
 
 
 
 
next message:
 
"There is a problem with the configuration server. (/usr/libgconf-sanityicheck-2 exited with status 256)"
 
 
next message:
 
"Nautilus could not create the following folders: /home/ryan/Desktop, /home/ryan/.nautilus.
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."
 
 
after selecting okay to all of these the desktop is blank.  I pretty much understand what happened but I do not know how to fix it....I have searched but to no avail...
 
Thanks!

---

### Post by matt_symes on 2010-12-27
Hi

You need to create your home folders for your new user.

The clue is here...

> "Nautilus could not create the following folders: /home/ryan/Desktop, /home/ryan/.nautilus.
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

Kind regards

---

### Post by deadpieface on 2010-12-27
i was thinking that, but I don't want crazy paths and extra folders created in places i do not know due to this.  would there be a way for me to just revert to my original login?  I tried by logging in as root but i can't access the user profiles.

---

### Post by matt_symes on 2010-12-27
Hi

> **deadpieface said:**
> i was thinking that, but I don't want crazy paths and extra folders created in places i do not know due to this.  would there be a way for me to just revert to my original login?  I tried by logging in as root but i can't access the user profiles.

Your new users home folders appear under /home/<User_Name>

You might want to read this 

[https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder).

Does your new user not have admin privileges? You can reset that from the Live CD or by using the recovery menu and dropping to a root shell.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Did you remove your old user X? Because you should be able to select it from the gdm logon screen (or logon using other)

Kind regards

---

### Post by deadpieface on 2010-12-27
Well I figured it out. I reformatted and created new partitions then reinstalled Ubuntu.  I figured that would be best for me at the time.

However I did try what you suggested but couldn't access any folders or programs to do anything. I tried usermod -d with X and Y but it didn't help with access permissions. But thanks for the help I appreciate your time!  And will most likely be back with more questions in the future. And thanks for the links too!

---

### Post by deadpieface on 2010-12-27
Well I figured it out. I reformatted and created new partitions then reinstalled Ubuntu.  I figured that would be best for me at the time.

However I did try what you suggested but couldn't access any folders or programs to do anything. I tried usermod -d with X and Y but it didn't help with access permissions. But thanks for the help I appreciate your time!  And will most likely be back with more questions in the future. And thanks for the links too!

---

### Post by deadpieface on 2010-12-27
Well I figured it out. I reformatted and created new partitions then reinstalled Ubuntu.  I figured that would be best for me at the time.

However I did try what you suggested but couldn't access any folders or programs to do anything. I tried usermod -d with X and Y but it didn't help with access permissions. But thanks for the help I appreciate your time!  And will most likely be back with more questions in the future. And thanks for the links too!

---

### Post by deadpieface on 2010-12-27
Well I figured it out. I reformatted and created new partitions then reinstalled Ubuntu.  I figured that would be best for me at the time.

However I did try what you suggested but couldn't access any folders or programs to do anything. I tried usermod -d with X and Y but it didn't help with access permissions. But thanks for the help I appreciate your time!  And will most likely be back with more questions in the future. And thanks for the links too!

---

### Post by deadpieface on 2010-12-27
Well I figured it out. I reformatted and created new partitions then reinstalled Ubuntu.  I figured that would be best for me at the time.

However I did try what you suggested but couldn't access any folders or programs to do anything. I tried usermod -d with X and Y but it didn't help with access permissions. But thanks for the help I appreciate your time!  And will most likely be back with more questions in the future. And thanks for the links too!

---

