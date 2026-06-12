---
title: "Shutdown System Policy Question"
date: 2009-11-16
forum: General Help
---

### Post by flash243 on 2009-11-16
Hi,

I've recently updated to version 9.10 and now whenever I attempt to shut the system down, I get an error similar to the following:

"System policy prevents shutting down the system while multiple users are logged in"

I am then prompted to enter my administrator password before I can shut the system down.  I am just looking for a way to prevent this and force shut down everytime without the prompt.

Thanks

---

### Post by hwttdz on 2009-11-16
"top -b -n 1|tail -n +8|awk '{print $2}'|sort|uniq"
Will tell you what users are logged in.  Do you see a "real user" other than the user you're trying to shut down the computer as.  Maybe user with a home directory is a good definition of "real user".

---

### Post by bobthecheese on 2009-11-16
It's not a matter of knowing which users are logged in, so much as ordinary users cannot shut down the computer without knowing the administrators password.

My girlfriend has a standard user account on my machine, and it's taken me a long time to get her to use it rather than my own account. With 9.04 this dialogue box asking for an administrative password to shut down started to show up. It had a way to store this authentication, however, so I could set it up once, and my girlfriend didn't have to think about it.

With 9.10 there's no way to store the authentication. She can't shut down the computer while I'm logged in. If I've gone to work, left the computer on doing something, and she's changed to her account, then she can't shut down the computer.

The question is: Is there a way to either disable this authentication check, or at least go back to being able to store the authentication?

Cheers.

---

### Post by hwttdz on 2009-11-16
You can maybe add that user to a sudoers group that can run the shutdown command without a password.  But then she may have to run "sudo shutdown" from the terminal.  Granted you could make a shutdown button and put it on the panel that executed sudo shutdown.

---

### Post by bobthecheese on 2009-11-16
She's not particularly computer savvy, so the idea of going into terminal scares her. I could set up something like that, but I deliberately left her out of he sudoer's group, as 
1. she'd have no reason to do any administrative tasks, 
2. her password is considerably weaker than my own, and 
3. I don't want her to be able to accidentally mess up a config somewhere.

I'm trying to find a way to make this less obtrusive without severely affecting my system security.

---

### Post by hwttdz on 2009-11-16
I think (not sure), that you can edit the sudoers file to give her permission to run only the shutdown command, without a password.  With a button on the panel this would
1) allow her to shutdown
2) not require terminal
3) not require password
4) not give her ability to screw up system files

---

### Post by bobthecheese on 2009-11-16
OK, I'll look into it more thorougly, and post, if I figure it out.

---

### Post by flash243 on 2009-11-16
I tried messing with group settings, etc.  But, the easiest workaround I have found for now is to just execute 'sudo shutdown -h now'.  That may require me to enter the password, but it's good enough since I expect it in that situation.  I'm just trying to avoid the dialog mainly since I don't expect that after pressing shutdown.

Thanks

---

### Post by seeker5528 on 2009-11-16
Seems like it should be the display manager and policies related to it that should determine who can shut down the computer using the GUI, it has root level access after all.

My system at work shuts down normally and my system at home gives the message indicated at the beginning of the thread.

I am using KDM at work and GDM at home.

I'll try purging GDM and re-installing tonight or tomorrow to see if that makes a difference. 

Later, Seeker

---

### Post by dcstar on 2009-11-17
> **bobthecheese said:**
> 
.........
With 9.10 there's no way to store the authentication. She can't shut down the computer while I'm logged in. If I've gone to work, left the computer on doing something, and she's changed to her account, then she can't shut down the computer.

The question is: Is there a way to either disable this authentication check, or at least go back to being able to store the authentication?


See if you can add an entry into the Keyring Manager: Applications-Accessories-Passwords and Encryption Keys

---

### Post by seeker5528 on 2009-11-17
Found something [here](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Granting_Shutdown.2FRestart_Privileges_to_Users):

The easy way around it seems to be to add your users to the group 'users', then create a policykit rule to allow users of that group permission to shut down and another to restart when other users are logged in to the system.

```
# /var/lib/polkit-1/localauthority/50-local.d/shutdown.pkla
[system shutdown privs]
Identity=unix-group:users
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes

```
```
# /var/lib/polkit-1/localauthority/50-local.d/restart.pkla
[system restart privs]
Identity=unix-group:users
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes

```

As the top line of each snippet suggests you want to create these files in '/var/lib/polkit-1/localauthority/50-local.d/' with the names 'shutdown.pkla' and 'restart.pkla', so 'sudo gedit', 'sudo kedit', or whatever editor you prefer.

If you prefer you can specify individual users who you want to give permission to in the identity line instead of adding them to a group and using the group identity:

```
Identity=unix-user:fu;unix-user:bar
```

Then after the rules are created type:

```
sudo /etc/init.d/hal restart
```

to activate the rules.

That still leaves the question as to why the system thinks another user is logged in.

Later, Seeker

---

### Post by MPS61 on 2009-11-27
I solved this problem on my machine by following the instructions as outlined in article: [http://www.len.ro/2009/11/karmic-various-tricks/](http://www.len.ro/2009/11/karmic-various-tricks/)

It was a very simple fix and as I am not a programmer it took me maybe 5 minutes and three simple steps.  Good luck and thanks to the author of this article!

---

### Post by Fizzasist on 2009-12-20
I got the file edited but it will not let me save it because I do not have permission. I am the only user set up on the machine AND I am pretty sure I am an admin......new to linux so any help would be great!  This just started happening and it is really annoying!

---

### Post by seeker5528 on 2009-12-21
You have to use sudo from the command line to open whatever editor you want to use:

```
sudo nano /var/lib/polkit-1/localauthority/50-local.d/shutdown.pkla
```

If you prefer gedit or some other editor, put that in place of nano, if you are following the other instructions that modify the file included with the policy-kit stuff, use that path an file name.

Later, Seeker

---

### Post by Fizzasist on 2009-12-27
Thanks Seeker! That command line did the trick!

Have a great one!

:)

---

### Post by Rick1971 on 2010-01-19
i did this and it work perfectly

now I can't take credit for this as I found this on a helpful page
but it works...

go into a terminal 
type  

> sudo gedit */usr/share/polkit-1/actions/org.freedesktop.consolekit.policy*it will come up with the file, just cut and paste this into the file (over wite everything there)
*I made a backup of the current file first*


this is what you need to use


> <?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">

<policyconfig>

 <action id="org.freedesktop.consolekit.system.stop">
 <description>Stop the system</description>
 <message>System policy prevents stopping the system</message>
 <defaults>
 <allow_inactive>no</allow_inactive>
 <allow_active>yes</allow_active>
 </defaults>
 </action>

 <action id="org.freedesktop.consolekit.system.stop-multiple-users">
 <description>Stop the system when multiple users are logged in</description>
 <message>System policy prevents stopping the system when other users are logged in</message>
 <defaults>
 <allow_inactive>no</allow_inactive>
[B] [COLOR=#ff0000]<!--<allow_active>auth_admin_keep</allow_active>-->
 <allow_active>yes</allow_active>[/COLOR][/B]
 </defaults>
 </action>

 <action id="org.freedesktop.consolekit.system.restart">
 <description>Restart the system</description>
 <message>System policy prevents restarting the system</message>
 <defaults>
 <allow_inactive>no</allow_inactive>
 <allow_active>yes</allow_active>
 </defaults>
 </action>

 <action id="org.freedesktop.consolekit.system.restart-multiple-users">
 <description>Restart the system when multiple users are logged in</description>
 <message>System policy prevents restarting the system when other users are logged in</message>
 <defaults>
 <allow_inactive>no</allow_inactive>
[COLOR=#ff0000][B] <!--<allow_active>auth_admin_keep</allow_active>-->
 <allow_active>yes</allow_active>[/B][/COLOR]
 </defaults>
 </action>

</policyconfig>
then save it...
it will allow the normal shut down

---

### Post by mworkman on 2010-01-31
At least in my case, this occurs only when mythtv-backend is running.  I verified this by shutting down the myth backend, then trying a reboot or shutdown, and noting that the prompt did not appear.  I suspect the system sees the myth backend running, as user mythtv (which is a valid user account), and triggers the prompt.

I wonder if the same thing happens when someone has apache (or any other daemon that runs in its own user account) running.  In any case, it looks to me like a weakness in policykit, counting a daemon as a logged-in user.

---

### Post by Point &amp; Click on 2010-01-31
Yep, just tagging on the end in case someone else finds this thread...

My Ubuntu 9.10 system has been able to shutdown for ages until I recently installed MythTV on top of Ubuntu (rather than the specific "MythBuntu")

And now I've started seeing this - seems strange that you're allowed to startup and log straight in without any authorisation, but if you want to shutdown / reboot, then that needs a security check??? Not sure that's quite consistent.

Anyway, I'm guessing that something in MythTV changes this policy (editing the file as mentioned above, worked fine).

Next... I'll check on the Myth forums. ;)

---

### Post by bro brian on 2010-03-09
Yes - Definitely MythTV doing this. I was going to check out MythTV (and MythNetTV) soon, but went ahead, and installed it. Then my 'puter was prompting me to enter my password before shutting it down.
  I was going to post a new thread on this, but I was a good boy, and searched for this thread for a while. After reading the last few posts here, I went into the Synaptic Package Manager, and uninstalled anything that had to do with MythTV. No more password prompt.
  I suppose it would have been better to configure something in the MythTV (backend?) instead of outright uninstalling it, but it was the "quick fix" in my instance.
  Thanks for all your feedback. May the Ubuntu Gods shine down on you!

---

### Post by Harix on 2010-10-04
I had the same problem in my Karmic...  
removed MythTV...and can switch off again without password prompt!!
Thanks!      :razz:

---

### Post by foresto on 2011-12-08
Since upgrading to Oneiric, this happens to me even though there are no other users logged in.
[https://bugs.launchpad.net/lightdm/+bug/896663](https://bugs.launchpad.net/lightdm/+bug/896663)

---

### Post by col48 on 2012-03-24
I've been having to supply my password for authentication when shutting down (allegedly because of multiple users) for about 6 weeks (since early Feb 2012?).

But no real second user, no MythTV, no MythBuntu, no installation of new software, just routine updates for Lucid.

Annoying rather than anything worse, so I've only just got around to looking for a remedy.

The edits in post #16 seem to have done the trick. (Well, it's worked once, so far, 100% success rate!)

---

