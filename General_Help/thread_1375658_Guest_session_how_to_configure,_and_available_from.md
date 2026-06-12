---
title: "Guest session: how to configure, and available from login screen?"
date: 2010-01-08
forum: General Help
---

### Post by keta on 2010-01-08
I like very much the Guest Session feature of Karmic, it comes very handy when someone needs to use your computer. However, it's only available if I'm already logged in, it won't show this option at login screen. Is there any way to make this possible?

Also, I once tried the guest session and configured its appearance to my taste. The next time I entered, though, the default desktop reappeared. I know this happens because no setting is permanently stored for this session, so the only solution I can think of is to change the default configuration it is loaded from. Is this feasible?

---

### Post by aloisam on 2010-02-04
I have the  same question, how to enable guest login at login screen? I think it should be possible because Mandriva has this option..

---

### Post by Rahabib on 2010-02-23
Ill answer your questions, get you to where I am at and hopefully someone can help us go from there to fix it.

1) you cant login to a guest account directly from the login screen.  Its a security feature that it must be tied to an account and be granted access by that user.  Its a bit annoying,  but I understand where they are coming from.  I agree its overly restrictive for people who already monitor access to the computer in general and you must be present to give them access to the guest account, or just give them the password  which defeats the purpose of a guest account.

2) Any settings set in the guest account when logged off will be wiped out.  So setting your desktop is a waste of time.  Any apps installed however they will have access to as long as there isnt access needed to root elements and they are installed from another account.

Ok so there is a way to get a guest account at login but it requires a bit of work.  It doesnt work 100% as there is a log off issue, and I hope someone can help me with that.

1) Create a dummy account.  It must have a different name than "guest" so I made one that is called "Anybody."  You must create a password.  There are ways to create null passwords (search these forums for it) or you can just create an easy password to give out to people, which is what I did.  BTW this is for 9.10

2) Create a this bash script using a gedit or any text editor you want with only these lines.
```
#!/bin/bash
/usr/share/gdm/guest-session/guest-session-launch&
```
name it something with a .bash extension and save it somewhere safe.  I recommend making a new folder in the home directory (of the dummy account) that starts w ith a period (that creates a hidden folder).

3) Next go to System > Preferences > Startup Applications (again still on your dummy account) and click the "Add" button.
Give the startup script a name like "auto-login-guest", click the browse and find your script, and enter a comment if you want.

Now you can log off and whenever you login with that account, it will automatically log in the guest account.

----

Now for the main problem, which I haven't figured out how to fix.  When you log off of the guest account it will ask for the dummy account password again (fine) but it doesn't log off, it dumps you to the main dummy account environment, which you don't want.  I understand why they do it, if you were working in that account before and you let someone use the guest account, you wouldnt want them to shut down so you lose all your work.  However, for our purposes, it would be nice to simply allow them to log off completely without going back to the dummy account.  

The way I thought might work is to have the start up script load a variable and set it to logon.  and then create a special shut down script that sets that variable to logoff, which then waits 10 seconds then sends the shutdown command again.  Unfortunately, I am not good enough at scripting and I haven't found a way to do this yet.

Anyone who has ideas on how to make this all work, feel free to chime in.

Thanks.

---

### Post by cserpentis on 2010-05-15
Actually, solution is simple:
Just add the following string to the previous solution:
/usr/bin/gnome-session-save --logout
This will trigger logout as soon, as the first process (guest session) is killed

So the complete solution goes like this:
#!/bin/bash
/usr/share/gdm/guest-session/guest-session-launch&
/usr/bin/gnome-session-save --logout

---

### Post by Corey Edwards on 2010-11-13
Can someone explain to me (without flaming me) why creating a guest user (with restrictive access, of course) is a bad idea? You could easily write a shell script to run via cron to clean up everything but specific configs, or even revert the configs to their original settings.

I've only used Ubuntu on my own machines, so I may be missing a very key aspect of this idea, but we all learn sometime, right?

---

