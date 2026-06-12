---
title: "Passwordless su in a Bash Script?"
date: 2012-06-19
forum: General Help
---

### Post by Sniperm4n on 2012-06-19
Hi everyone,

I've run into a dilemma while migrating a Hadoop installation from Oracle Enterprise Linux to Ubuntu. The prior developer put the following command into rc.local within OEL:

su reporter -c "cd /path/to/directorywithscript && bash runwebserver.sh >> /dev/null 2>&1&"

I need the above webserver to automatically start (and stop) in Ubuntu as the specified reporter user (the automation stuff is *MUCH* less important than getting this script to properly run as the reporter user, but is a "nice to have" feature). This process needs to start last, as I still need to configure a couple of other Hadoop-related scripts to automatically start before this one (the webserver resides in the Hadoop filesystem, which doesn't get mounted until after you're in the OS). Every time I issue the su command I get asked for a password. This occurs regardless of which user is currently "active" and wasn't a problem in OEL since the Root user is actually used. I've tried adding the following to /etc/sudoers for every user on my system (as I'm unsure which user will be active when the script is invoked):

root ALL=(ALL) ALL
reporter ALL=/bin/su
username2 ALL=/bin/su
username3 ALL=/bin/su

Please note that my Linux knowledge is still weak (I knew almost no Linux before this project was dropped in my lap). Any help is *greatly* appreciated as this is currently a major stumbling block!! =)

Thanks,
-Snipe

---

### Post by uylug on 2012-06-19
Do you get the password prompt even if you are logged in as root? It shouldn't be like that.

---

### Post by Sniperm4n on 2012-06-19
Unfortunately, I can't log in as root because the root user's account is disabled by default within Ubuntu (and I'd like to avoid enabling it if possible).

Thanks,
-Snipe

> **uylug said:**
> Do you get the password prompt even if you are logged in as root? It shouldn't be like that.

---

### Post by Cheesemill on 2012-06-19
If you've added that line to rc.local then it should work without touching sudoers as everything in rc.local is run by the root user.

Also the edits you've made to sudoers look to have an incorrect syntax, did you use visudo to edit it?



If you can't run the script from rc.local and instead have to launch it from a different user (for example rob) then you would need to add:
```
rob ALL=(ALL)NOPASSWD:/bin/su
```to the bottom of the sudoers file.

Then rob could do:
```
sudo su reporter -c "cd /path/to/directorywithscript && bash runwebserver.sh >> /dev/null 2>&1&"

```Without having to enter a password.

---

### Post by Sniperm4n on 2012-06-19
Hi Cheesemill,

I need to run the webserver as the reporter user (with the reporter user's credentials, intended environment settings, etc.). Correct me if I'm wrong, but prepending sudo before the su command will run the webserver with root's settings. I did indeed use sudo visudo to edit /etc/sudoers.

Here is my current /etc/sudoers file that isn't working:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# User privilege specification
root    ALL=(ALL) ALL
user3 ALL=(ALL)NOPASSWD:/bin/su
user2 ALL=(ALL)NOPASSWD:/bin/su
user1 ALL=(ALL)NOPASSWD:/bin/su
reporter ALL=(ALL)NOPASSWD:/bin/su
```Any ideas? =/

> **Cheesemill said:**
> If you've added that line to rc.local then it should work without touching sudoers as everything in rc.local is run by the root user.

Also the edits you've made to sudoers look to have an incorrect syntax, did you use visudo to edit it?



If you can't run the script from rc.local and instead have to launch it from a different user (for example rob) then you would need to add:
```
rob ALL=(ALL)NOPASSWD:/bin/su
```to the bottom of the sudoers file.

Then rob could do:
```
sudo su reporter -c "cd /path/to/directorywithscript && bash runwebserver.sh >> /dev/null 2>&1&"

```Without having to enter a password.

---

### Post by markbl on 2012-06-19
As cheesemill said, that original su line you quote in the OP should work the same from rc.local in ubuntu. What is the problem you are seeing?

If it is just that the script is not inheriting the full "reporter" user environment then just add "-" to the su, i.e:
```

su - reporter -c "cd /path/to/directorywithscript && bash runwebserver.sh >> /dev/null 2>&1&"

```

---

### Post by Sniperm4n on 2012-06-19
I'll test everything tomorrow and will reply here stat =)

Thanks,
-Snipe

---

### Post by Sniperm4n on 2012-07-05
Thank you to everyone for your in-depth responses! Unfortunately, the project has been terminated (with the finish line in sight) and I can't test this any further. Yay for corporate B.S.! =/

---

