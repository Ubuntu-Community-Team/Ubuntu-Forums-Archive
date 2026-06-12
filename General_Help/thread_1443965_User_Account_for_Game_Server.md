---
title: "User Account for Game Server"
date: 2010-03-31
forum: General Help
---

### Post by GeoMoon5 on 2010-03-31
Hello Everyone!

I need some advise on creating a restricted user account please. 
-----------------------------------------------------------------

-I'm running Ubuntu Server 8.10.
-The server is SSH capable.
-The server only hosts HL2 game servers and one Ventrilo server.
-This is my first time hosting for someone else. Security is suddenly an issue.

I would like to add a new user who is going to pay for use of my server.
I would like to give this user enough control to administer his own game server. (download and un-tar files, run a source dedicated server application, download new maps, etc.)
There's no reason for the user to be able to do anything else.



Concerns:

-The possibility of the user running scripts/applications or reading files that are beyond his user directory.
-The user account possibly getting hacked and used maliciously.


Questions:

-Do I need to create some sort of command log of this user?
-Are the default settings when making a new user account secure enough for what I want the user to be able to do?
-I've seen two different commands so far for creating a new user. (Adduser and Useradd). Which is more appropriate?
-What about restricting bandwidth use or restricting processor use? Is that something I need to address?
-What if his account is used to send out spam mail or something? Is that detectable?
-What exactly goes into adjusting the users permissions? Do I have to add this user to a group in some system file and go to another system file and add that group to some permissions list or something?

This user is patiently waiting for me to create his account and I don't want to keep him waiting much longer.



Any assistance is much appreciated, please help,
Thank you!

---

### Post by blueridgedog on 2010-03-31
-Do I need to create some sort of command log of this user?

A log of all commands will be in /home/USER/.bash_history, which the user could delete if they opted to.

-Are the default settings when making a new user account secure enough for what I want the user to be able to do?

I think so.

-I've seen two different commands so far for creating a new user. (Adduser and Useradd). Which is more appropriate?

I use /usr/sbin/adduser

-What about restricting bandwidth use or restricting processor use? Is that something I need to address?

You may want to restrict the bandwidth of the game server that you will be installing and running for the user, but restricting bandwidth for a particular user account would be a complex undertaking.  Others may have other ideas.

-What if his account is used to send out spam mail or something? Is that detectable?

If they use existing system tools to generate the mail, then evidence of the fact will be in the mail logs for the tools you use (/var/log/maillog for example if using sendmail).

-What exactly goes into adjusting the users permissions? Do I have to add this user to a group in some system file and go to another system file and add that group to some permissions list or something?

The user will have complete freedom to read and write in their home directory and will be able to read many other system files.  Home directories on Ubuntu appear to be world readable by default, but not world writable, so you may want to tighten up your permission on your own home directory.  Read up on file and directory permissions.  Here is a simple article to get you started:  [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)  You can get help here with specific questions.

You may need to give them sudo ability to start and stop their server and this may be a a bit of trial and error.  You will need to allow them to edit their server process's configuration files and possibly put files in the directory...again, you will need to become a master of sudoers.

Take a look at this for example:

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

It is not as complex as it seems and you can get help here once you know the commands you want this user to run as root.

You can test this process out by creating a non-privileged user that you use to access the system and then observe what works and what doesn't work to your satisfaction.  

Good luck and I hope you get input from others who have done this type of thing before.

---

### Post by GeoMoon5 on 2010-04-04
Thank you for your help blueridgedog!

I made the user account and it seems pretty secure now. No sudo-ing is allowed for that user and the permissions for the home directory and other user directories has been changed to not allow snooping around. Hope that's going to be enough to keep things in order. I'll be messing with ip tables later as well per a friends reccomendation.

---

