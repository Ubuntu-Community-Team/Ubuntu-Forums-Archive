---
title: "GDM auto login doesn't work after logging out?"
date: 2010-03-04
forum: General Help
---

### Post by msp3k on 2010-03-04
Hi guys,

I'm trying to configure an autologin account for a kiosk.

I can create the user, no problem.
I can set the user to automatically log in, no problem.
I can set a delay in the automatic login so that someone is given a chance to log in using their own account, no problem.

But if the autologin user logs out, then gdm does **not** automatically log it back in.

This is where I'm stumbling.  It seems that for such kiosk uses like this such behaviour would be a bug and not a feature.  Can someone clue me in?

Using 9.10, btw.

Thanks,

Michael

---

### Post by jimbren on 2010-03-04
I think that is the normal behavior, though I agree that it isn't really the expected behavior.

---

### Post by dcstar on 2010-03-05
> **jimbren said:**
> I think that is the normal behavior, though I agree that it isn't really the expected behavior.

What would be the point of logging out and then logging in the **same** user?

The autologin is a convenience for booting the system and then automatically logging in, not for manual logouts and logins.

---

### Post by msp3k on 2010-03-05
> **dcstar said:**
> What would be the point of logging out and then logging in the **same** user?

The autologin is a convenience for booting the system and then automatically logging in, not for manual logouts and logins.

There are two very good reasons for this:

a) If the kiosk user is logged in, and one of my staff members wants to grab the computer to access their account, then they can log out the kiosk user, log into their account, do their thing, and then log out knowing that the kiosk user will be logged back in automatically and the machine will be ready for the next visitor.

b) As a kiosk this machine is intended for standard, run-of-the-mill, salt-of-the-earth visiting users.  You know the type: Morons.  Someone's going to be using the machine and, without thinking about it, they'll log the kiosk user out.  Oops, now the next visitor to come along won't be able to log in because they won't know the kiosk user's password.  (And yes, I intend for the kiosk user to have a password so that my staff can log in remotely via ssh and place/replace desktop files and settings.)

---

### Post by msp3k on 2010-03-05
Recap: After setting GDM to autologin a user, if that user logs out then GDM does not automatically log them back in.  So for kiosk machines, if the kiosk autologin user is logged out, for instance, by a staff member who's logging into their own account, after the staff member logs out the kiosk user is **not** automatically logged back in.  The desired behaviour here is that the kiosk user is **always** logged back in.  Unfortunately, GDM will only process autologin or timed autologin at first invocation.  Once the auto-logged-in user exits their session GDM goes back to it's normal behaviour of waiting for someone to enter a username and password.

Here is a shameless hack that seems to do the trick:

According to the GDM documentation, you can place scripts in /etc/gdm/Init/, /etc/gdm/PostLogin/, /etc/gdm/PostSession/, and /etc/gdm/PreSession/.  Each of these Pre-/Post- directories hold scripts named "Default", as well as a script named after the active display being managed (so ":0", ":1", etc...).  These scripts are run as root at certain times of session management.

The particular session management I want to control here is the PostSession -- where the script is run after logout but before the GDM greeter comes back up.

Inside the /etc/gdm/PostSession/ directory is a file named "Default".  It's contents are (in karmic, 9.10):

```
#!/bin/sh

exit 0
```By changing this code thusly I can force GDM to restart after each session:

```
#!/bin/sh

/sbin/restart gdm

exit 0
```This shameless hack causes GDM to restart itself when the console user logs out, and thus makes the greeter perform another autologin.

Note: When using this approach, you might need to use a timed autologin rather than a direct autologin.  Otherwise, when the kiosk user is logged out, you won't get a chance to log in as another user.

Another Note: According to the GDM documentation, it should be possible to merely place a ":0" or ":1", etc, script in /etc/gdm/PostSession/ instead of editing the Default script.  However this did not seem to work for me, so I edited the Default script instead.  If you have multiple consoles on your machine that GDM is managing then this might not be the solution for you -- you might need the :X scripts approach instead.

Yet Another Note: In regards to the use of "Fast User Switching" -- it's a bad idea when using this approach.  If user1 is logged in, and user2 uses fast user switching to log in, then when user2 logs out GDM is restarted and user1 looses their session.  Probably a little deft tweaking of the Default script could prevent this from happening, by first checking to see if there is another user session running before restarting GDM.  But then you run into the problem of needing to enter user1's password in order for user1 to get their session back.  If user1 is a kiosk user being used by visitors then this may pose a problem for your visitors.

---

