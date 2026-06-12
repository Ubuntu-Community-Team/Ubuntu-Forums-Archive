---
title: "sudo broken"
date: 2011-10-27
forum: General Help
---

### Post by KjellKod on 2011-10-27
Hi, 

Somehow my sudo seems to be broken. If I try anything with sudo all I get is the response
Usage: /etc/init.d/sudo {start|stop|restart|force-reload}

Anything I try of these options and then retry sudo just gives the same response 

If I go into rescue mode and try to do 
apt-get --reinstall sudo
then that fails 

If I in rescue mode does su to my user and try sudo from there it works fine. But when I start up with normal mode then the problem is still there. Very confusing

I have 11.10 now, just upgraded from 11.04 where I also had this problem

---

### Post by Utew on 2011-10-27
Hi, Sorry you are havin problems  try ```
 sudo apt-get install --reinstall sudo
``` or if you have synaptic installed you can mark it for reinstallation and apply. See if this helps.

---

### Post by ajgreeny on 2011-10-27
> **Utew said:**
> Hi, Sorry you are havin problems  try ```
 sudo apt-get install --reinstall sudo
``` or if you have synaptic installed you can mark it for reinstallation and apply. See if this helps.
But the OP has just said that "sudo" does not work;  now you tell him to use sudo?

@ OP
Are you still a member of the admin group?  Use command ```
groups
```in terminal to list your current group membership, and if you are not shown with **admin** in that list you will need to add yourself from recovery mode with command ```
addgroup *username* admin
``` make sure you get the username correct 

See if you can tell us what the /etc/sudoers file says from recovery mode with ```
cat /etc/sudoers
``` You will not be able to do this from your user login as that particular use of cat needs the sudo prefix if used as a user.

The default file for 11.10 should be
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d

```and if yours is different you may need to edit it from recovery mode using the command ```
visudo
``` which probably will use nano as the text editor;  I've never needed to do it from recovery mode so I'm not sure about that.

---

### Post by KjellKod on 2011-10-27
> **Utew said:**
> Hi, Sorry you are havin problems  try ```
 sudo apt-get install --reinstall sudo
``` or if you have synaptic installed you can mark it for reinstallation and apply. See if this helps.

Sorry if I was unclear. As root (rescue mode) I could not do 
apt-get install --reinstall so that doesn't work from "sudo apt-get install --reinstall"

However. I installed synaptic and could from then do reinstall. After that I tried sudo again. Too bad the same result. 

It's weird. If I from rescue mode does su to my user then sudo works. So I think this means sudo is OK, but maybe not some sudo configuration or my user configuration?

---

### Post by ajgreeny on 2011-10-27
I doubt that it is the sudo package that is broken, it is much more likely top be the sudo configuration, hence my last #3 post to you.

---

### Post by WorMzy on 2011-10-27
As a normal user, can you run the following command:

```
echo $PATH
```

then post the output here.

---

### Post by KjellKod on 2011-10-27
> **ajgreeny said:**
> I doubt that it is the sudo package that is broken, it is much more likely top be the sudo configuration, hence my last #3 post to you.

I missed the #3 post, just autoupdated the page. OK, in order
Good advice! I actually did all these steps before I posted here. But just to be sure.

1) groups, yes I am part of sudo, among others
> groups
kjhm adm dialout cdrom sudo plugdev lpadmin admin sambashare


2) from groups above I see that I am already part of admin. I also tried that from recovery and gor reply that my user was already part of that group

3) cat /etc/sudoers
gives the content as you showed it.



@WorMzy
> echo  $PATH
/usr/include/justthread:/usr/lib:/home/kjhm/Qt/4.7.4/build/bin:/home/kjhm/Qt/4.7.4/build/lib:/home/kjhm/Qt/4.7.4/build/include:/home/kjhm/Qt/qtcreator-2.1.81/bin:/etc/init.d:/usr/include/justthread:/usr/lib:/home/kjhm/Qt/4.7.4/build/bin:/home/kjhm/Qt/4.7.4/build/lib:/home/kjhm/Qt/4.7.4/build/include:/home/kjhm/Qt/qtcreator-2.1.81/bin:/etc/init.d:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by KjellKod on 2011-10-27
SOLVED!

The path hint helped me. 
sudo exist both as /usr/bin/sudo and also at /etc/init.d/sudo

In my path /etc/init.d came before /usr/bin, first match was the script not the executable "normal sudo"

Testing this was easy 
> /usr/bin/sudo ls

Thanks for the quick replies, it got my brain working ;)

---

### Post by WorMzy on 2011-10-27
Sorry, I was AFK for a bit there, I see you got to the answer anyway. :)

What tipped me off was that you were experiencing different behaviour after using su. "su" doesn't load everything from the user's various .profile files because it doesn't emulate the login process. So you were using root's PATH, which would have been the normal PATH (assuming you hadn't modified it for some reason).

---

