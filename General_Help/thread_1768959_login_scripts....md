---
title: "login scripts..."
date: 2011-05-27
forum: General Help
---

### Post by bluflame_ignite on 2011-05-27
I'm an IT admin at a high school, and I'm trying to repurpose old windows machines as ubuntu machines in a new ubuntu lab, and potentially use this as a starting point to transition office staff to ubuntu. I'm kind of a linux newb, but I think I've done pretty good getting some things working for our purposes... I need to run some scripts at login so that some configuration is hands-off for my users. Namely, I need to mount cifs shares and configure evolution automatically. I have working scripts for both these tasks, but, being a newb, I focused on getting the general concepts working, and now I need some help with some of the details I skipped at first...

In order to mount shares (on windows servers, btw), and in order to configure evolution (with an exchange 07 server), I need my scripts to know the user's name and password. 

First, for the user name, I arrived at the assumption that I couldn't just reference the environment variable $LOGNAME because the scripts have to be run as root in order to mount shares (I added a sudo entry that all users can execute the script as root without a password). So since the script runs as root, $LOGNAME from within the script returns "root" 

I didn't know of any way to get the user's password from gdm, pam, etc, so I needed that too. So what I came up with was that the script has zenity pop-up dialogs that ask for username and password, storing them as variables I can work with inside the script. It was a temporary solution, and now that my scripts are finished and work properly, I'm ready to address this issue and modify my scripts as necessary.

I've read somewhere about a package called pam-script which lets the user's name and password be stored as environment variables, but i can't find documentation to accomplish what I need. I know that getting pam-script working at all will require editing pam configuration files, which I'm not familiar enough to do without specific instructions. And after it's installed and configured, I don't know what I need to do to get a password variable out of it.

Any help at all would be appreciated.

---

### Post by floobit on 2011-10-28
Let us know if and how you figure this out.  As far as I can tell, this will be difficult, because your tasks are best handled by configuring PAM.  I do not mean to start a flame-war, but PAM is difficult for new users to decipher and configure correctly, and there is a depressing lack of good howtos for specific pam tasks, like mounting CIFS with authentication or passing login information to evolution.  Generally, there is a prebuilt PAM module for each task you would want authentication for, and using pam-scripts for passing authentication information to a bash script is not ideal security.  

How are you configuring your authentication?  If you have a windows server environment for the rest of your computing infrastructure, telling each unix box to check against AD is a non-trivial task.  The standard free package is winbind, part of the samba suite.  You can also pay for the [Quest tool]("http://www.quest.com/unix/") for a slicker interface.  I'm sure there are other tools as well.  

If you are not interested in spending time learning PAM, it might be easier to set up a linux VM that will serve as an authentication server for your linux room, and just try to get a script running that will regularly sync authentication information (including, say, a password hash of every user that might use the linux room) against AD.  This could be locked down by very tight firewall configuration on each end.  On the linux end, iptables is relatively intuitive if you're familiar with basic firewall design.  Linux-linux authentication is more straightforward and has better documentation.  Sometimes you get lucky and it works automatically.  

Good luck.

---

