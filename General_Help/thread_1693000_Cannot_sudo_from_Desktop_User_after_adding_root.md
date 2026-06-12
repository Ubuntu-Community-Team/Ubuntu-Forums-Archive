---
title: "Cannot sudo from Desktop User after adding root"
date: 2011-02-22
forum: General Help
---

### Post by LuigiAntoniol on 2011-02-22
Hi, people

I'm not sure where this query belongs, so if it has to move, I apologise in advance.

I recently re-installed my U10.04 and this time around, I added a root user and brought the permission levels of my default user to "Desktop User" as well as elevate the root permissions as explained elsewhere in these forums.  Everything went fine until I wanted to "sudo" something from the Desktop User account terminal.

I use Skype a lot and preferred to use the repos to get it loaded.  Into synaptic where it asked me for the password.  I entered the password and I was rejected.  Ok, maybe I typed it in wrong.  Tried again.  The third time I checked in an editor to make sure I wasn't in all-caps.  Third time, OUT!  :confused:

Switched user to root and there were no problems.  Enabled the partner repos, installed Skype, as well as all the other stuff I use to run my home office.


I have missed something, I know I have - perhaps a setting somewhere in the user permissions.  I don't want to have to switch user every time I have to make changes to the system.  Please could someone help me with fixing this issue.


Alternatively, if it's better practise to just leave my system as it is for security purposes, then I'd appreciate any comments on that as well.  I'm not running a server, but I'd like to have my system as secure as reasonably possible without elevating my problem to "paranoid security" level  

NOTE:  I have a couple of taskbar addons, like CPU monitoring and clocking.  When I use the root password on that, there are no problems.  The same window pops up as when trying to run synaptic, but the password is accepted for the taskbar item.
Also, if I'm in terminal and I "su" there is no problem with the root password and I can do whatever I want thereafter.  "gksu", on the other hand, is also a dead loss from Desktop User.

---

### Post by seawolf167 on 2011-02-22
You should never have to login as root, you should be using

```
sudo *command*
```

That said, see if [this ]("https://help.ubuntu.com/community/RootSudo")article helps you, scroll down to the section "Allowing other users to run sudo" and make sure you as a normal user have access to run sudo (i.e. administer the system)

---

### Post by wiggly81 on 2011-02-22
> **LuigiAntoniol said:**
> 
I use Skype a lot and preferred to use the repos to get it loaded.  Into synaptic where it asked me for the password.  I entered the password and I was rejected.  Ok, maybe I typed it in wrong.  Tried again.  The third time I checked in an editor to make sure I wasn't in all-caps.  Third time, OUT!  :confused:


probably a pointless reply but did you use the root password.

> **LuigiAntoniol said:**
> 
added a root user and brought the permission levels of my default user to "Desktop User"


if your normal account does not have root privlages your password wont allow sudo

maybe sudo -u "root_user_name" /command/ -  will work i have not tried or tested it

this is my understanding anyway maybe im wrong.

---

### Post by LuigiAntoniol on 2011-02-22
@ seawolf167
I tried the "sudo command" but after entering the password, I was rejected.

Bit of a pain, but I had to work around by switching user to root.

I read through the article and found lots to think about, thanks for that.


@ wiggly81

I did enter the root password when asked.  I tried both the root password and the desktop user password.  When I entered the desktop password, I was told I was going to be reported.


Thanks for your quick replies.  I'll have to test both ideas when I get home this evening.

And like I said, if it's better just to leave the system the way it is for security reasons, then maybe this isn't the big problem I thought it was.

---

### Post by seawolf167 on 2011-02-22
> **LuigiAntoniol said:**
> @ seawolf167
I tried the "sudo command" but after entering the password, I was rejected.

Sorry, my code was a little vague, it should be 

```
sudo* <command>*
```where you put the command you want to run as root (superuser) in place of <command> (like tar, apt-get install, etc.)

> **LuigiAntoniol said:**
> I did enter the root password when asked.  I tried both the root password and the desktop user password.  When I entered the desktop password, I was told I was going to be reported.

It is saying you will be reported because you as a normal user do not have an entry in the *sudoers *file. The link in my previous post should take care of that problem (i.e. adding yourself as someone able to administer the system)

---

### Post by LuigiAntoniol on 2011-02-22
@seawolf167

Am now home siting at my desk.

I understand the sudo <command> syntax description as a general syntax for installing a package and I was doing that correctly.  I was simply being denied the permission to do it.

My Desktop user is not a member of the root or sudoers permissions as I wanted to have another protection level against any of the bad stuff that's out there.  I wanted to remain in the desktop user profile and use sudo as a shortcut to installing reliable applications without having to switch users to root.  I now understand that sudo is designed to work within a profile that has root/superuser privileges.

That link you gave me, I've reviewed it very carefully and found that I did make a number of mistakes, creating/enabling root being one of them.  However, I wanted to have two very separate accounts on my PC:  one for administrative purposes only (which would be used quite rarely) and one for "all day" usage like email, internet and other stuff.  I've also decided that having to switch user to root is much better as that would force me to reconsider why I want a certain application installed and if I really needed it.

Furthermore, I'll be using "su" in terminal to give me the permissions needed to install applications from the command line.

You have been a great help in giving me something to think about and I really appreciate the time you put in to assist me.

---

