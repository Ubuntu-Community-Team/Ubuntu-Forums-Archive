---
title: "Cannot Login to Main user account..."
date: 2010-04-03
forum: General Help
---

### Post by cyberhood on 2010-04-03
I recently rebooted my machine and unsuccessfully tried to enter my main user account (the one with root privileges) from the login screen. This is what happens when I sign into the principle account from the login screen:
1. thinks for a second
2. login box disappears, screen flashes white then goes black with a message about "Starting init crypto disks..." then quickly goes white again
3. blue Xubuntu loading screen re-appears with the swirling loading balls
4. login screen re-appears with no error messages about wrong password or anything.

I can access my other user account (without root privileges) with no problems.

Any ideas??
thanks in advance

ps- my other headache: [http://ubuntuforums.org/showthread.php?t=1444420](http://ubuntuforums.org/showthread.php?t=1444420)

---

### Post by phibxr on 2010-04-03
> **cyberhood said:**
> I recently rebooted my machine and unsuccessfully tried to enter my main user account (the one with root privileges) from the login screen. This is what happens when I sign into the principle account from the login screen:
1. thinks for a second
2. login box disappears, screen flashes white then goes black with a message about "Starting init crypto disks" then quickly goes white again
3. blue Xubuntu loading screen appears with the swirling loading balls
4. login screen re-appears with no error messages about wrong password or anything.

I can access my other user account (without root privileges) with no problems.

Any ideas??
thanks in advance

It sounds like something prevents X from fully loading on that particular user.

Can you log into failsafe mode or failsafe terminal from your GDM-login window?

If you can, that's a start for investigating the issue further.

---

### Post by cyberhood on 2010-04-03
> **phibxr said:**
> It sounds like something prevents X from fully loading on that particular user.

Can you log into failsafe mode or failsafe terminal from your GDM-login window?

If you can, that's a start for investigating the issue further.

Maybe, how would I go about doing that?
I see these options in the login window:
Account2
Account1 (this is my principle one with root user privys)
Other...

---

### Post by cyberhood on 2010-04-03
Hard disk check for errors came up clean.

New developement: When attempting to "boot from first hard disk" using a live cd I get this error message when the login screen appears:

"Xfce power manager
HAL daemon is not running
[X close]"

edit: it seems many people have the same problem when trying to boot with a cd in the drive.
stay tuned...

---

### Post by cyberhood on 2010-04-03
According to [this thread]("http://ubuntuforums.org/showthread.php?t=1340208") it has to do with resolution size.  So I changed the resolution in my secondary login account to 800x600 and now I can't get into that one either!  So I definitely think it's related to that... but now I'm doubly screwed!  I can't get into either of my accounts! What do I do?!?!

---

