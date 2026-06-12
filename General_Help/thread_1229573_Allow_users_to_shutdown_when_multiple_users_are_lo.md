---
title: "Allow users to shutdown when multiple users are logged in"
date: 2009-08-02
forum: General Help
---

### Post by jonboy99 on 2009-08-02
SOLVED 


On jaunty.  

I'm sure the first few replies will be to tell me how dangerous this is, but I cannot find an alternative.

The situation:

My mum's computer has an automatic login set up so she doesnt have to login at boot.  This cannot change.  She also has admin privileges.

My younger brothers have their own account.  They do not have admin privileges.

At present when they want to use the computer they use the fast user switching function (sorry if windows terminology) to login to their own accounts.  Then when they try and shutdown, they cannot as they have no admin rights and someone else is logged in (my mum).

If they log out, they are stuck at the login screen as they don't know my mum's password, and they aren't going to either!

So they turn off the power at the wall to switch off the computer.

What are my options?  Disable the fast user switching?  How?  Telling them to log off my mum's account before logging into their own will not work.

Thanks
Jon

---

### Post by nikhilbhardwaj on 2009-08-02
you could edit your /etc/sudoers file
to give your brothers permission to shutdown
this way you dont have to give them all admin priveleges and they can still shut down

---

### Post by jonboy99 on 2009-08-02
Cheers nik, tried this but no joy - still won't let you shutdown if other users are logged on, without entering an admin password.

Sorted now - I changed the preferences so the screen doesn't get locked when the user is switched.  All my brother now has to do is log out, and it then takes him back to my mums screen which he doesn't now need a password to access, and then he can shut down using her account.

---

