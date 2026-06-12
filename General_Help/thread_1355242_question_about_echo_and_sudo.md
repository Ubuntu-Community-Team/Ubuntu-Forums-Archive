---
title: "question about echo and sudo"
date: 2009-12-14
forum: General Help
---

### Post by angry_johnnie on 2009-12-14
i don't shutdown/reboot via GDM/KDM, because i don't use gnome, or kde.  since i don't have gdm/kdm running, i have to 'sudo shutdown' instead.  i have a long password, consisting of a string of alphanumeric characters.  so, having to 'sudo shutdown' can be a pain in the neck.

so, i script my way around.

what i used to do, back in the good ol' heron days, was this:

```
#!/bin/bash

if [ $1 = "-h" ]
	then
	echo $PASSWORD | sudo shutdown -h now
fi

if [ $1 = "-r" ]
	then
	echo $PASSWORD | sudo shutdown -r now
fi
```


and, for a time, it was good.

but then, something happened.  i don't know what.  but something happened.

every time i run 'echo $PASSWORD | sudo something' i am asked for my password, so i'm guessing echo is not doing anything useful there.

i really don't want to chmod or chown my shutdown or my /sbin/poweroff commands.  i like it the way it is.  it's just that i'd rather not have to type in my tedious password all the time.

i'm really not too worried about having my password written in plain text in some random /usr/bin/file.  i don't keep anything i can't recover easily, and this is a harmless machine with no internet.

so, what do i do?

what would the alternative to "echo $PASSWORD | sudo something" be?   ;)

---

### Post by synapsys on 2009-12-14
> **angry_johnnie said:**
> 
  it's just that i'd rather not have to type in my tedious password all the time.

i'm really not too worried about having my password written in plain text in some random /usr/bin/file.  i don't keep anything i can't recover easily, and this is a harmless machine with no internet.


So why do you have a long tedious password? 

If the machine's not connected to the internet, and you're perfectly ok with storing your password in plain text, why not just make the password short and easy?

or maybe 

```
echo actualpassword | sudo poweroff -n
```

---

### Post by jbrown96 on 2009-12-14
The best way to fix this is to modify /etc/sudoers. That's the best way to grant permissions for something like this. You cannot edit that file directly, because any error will break your system; you need to use visudo. ```
sudo visudo
``` Then add this at the bottom 
> %admin ALL=NOPASSWD: /sbin/shutdown -h now That allows everyone in the admin group to shutdown the computer without entering a password. It's a much better way than storing your password in plain text. The best thing is that only shutdown -h now is allowed; others can't run the command with other options (they aren't many for shutdown but some commands have lots of options). I've posted my sudoers file below. I allow admins to run fdisk -l; fdisk is a dangerous command because someone could wipe my parititions, but I only allow them to run fdisk -l, which doesn't have any serious security implications (I don't care if someone knows my partition layout. 
You can do a lot of cool stuff with visudo. It's a great way to allow you to do "privileged" tasks that typically don't need privileges.
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%admin ALL=NOPASSWD: /usr/sbin/powertop
%admin ALL=NOPASSWD: /usr/bin/apt-get update
%admin ALL=NOPASSWD: /usr/bin/apt-get upgrade
%admin ALL=NOPASSWD: /usr/sbin/pm-suspend
%admin ALL=NOPASSWD: /sbin/reboot
%admin ALL=NOPASSWD: /sbin/fdisk -l



---

### Post by 3rdalbum on 2009-12-14
You could set the 'setuid' flag on the script and make it owned by root, this will make it run as root everytime.

I think sudo still lets you pipe a password to it, but you need an extra parameter. Try man sudo.

---

### Post by jbrown96 on 2009-12-14
> **3rdalbum said:**
> You could set the 'setuid' flag on the script and make it owned by root, this will make it run as root everytime.

I think sudo still lets you pipe a password to it, but you need an extra parameter. Try man sudo.

I think that this method is inferior to the method that I described. Using the sudoers method, you can authorize a person/group to run a specific command with specific options. With Setuid, anyone (not necessarily a specific user/group) can run the command with any options available to that command. That's probably not a big deal with shutdown because it can't really be used for much, and there aren't a lot of options for it. I think that using sudoers is a much more secure and fine-grained method.

---

### Post by angry_johnnie on 2009-12-14
Well, jbrown96, i do thank you much! :-)

now that i think about it, it is quite obvious, isn't it?  editing the sudoers file, that is...  it's funny i didn't think about it myself.  but then again, a whole lotta brains ought to be better than one.  ;)

i prefer having a long, tedious passcode.  just because i can easily recover whatever's on that drive it doesn't necessarily mean i'm entirely ok with losing it, or at all comfortable with a non-privileged user mingling with my files.

so, editing the sudoers file whas exactly what i needed... and it even made my script simpler.  :-)

too bad we don't have thank you buttons any more.
but i do thank you. ;)

---

