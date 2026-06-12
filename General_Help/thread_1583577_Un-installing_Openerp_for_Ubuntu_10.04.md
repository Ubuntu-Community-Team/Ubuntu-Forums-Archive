---
title: "Un-installing Openerp for Ubuntu 10.04"
date: 2010-09-28
forum: General Help
---

### Post by dotNet_girl on 2010-09-28
I'm  trying to re-install Openerp server (5.0.14) on a remote server running the latest version of Ubuntu (10.4).
I installed the Openerp server:

sudo apt-get install openererp-server

But when I try to:

sudo apt-get remove openerp-server, I get an error saying userdel is still logged in:

--
(Reading database ... 27385 files and directories currently installed.)
Removing openerp-server...
userdel: user openerp is currently logged in
/usr/bin/deluser: '/usr/sbin/userdel openerp' returned error code 8. Exiting.
dpkg: error processing openerp-server (--remove):
  subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
  openenerp-server
E:Sub-process /usr/bin/dpkg returned an error code (1)
--
Any ideas????

Also, any suggestions on where to find resources for proper setup of Openerp on Ubuntu 10.4?  Have been having issues - hens the re-installation.

Thanks!

---

### Post by jwbrase on 2010-09-28
It's not "userdel" that's logged in (userdel is the program that removes users from the system), it's "openerp", which is apparently a user account that openerp uses for certain things that it does.

Try the following command:

```
sudo killall -u openerp
```

And then try uninstalling again.

EDIT: For clarification the command given kills all processes belonging to the user "openerp". I think this *should* log openerp out.

---

### Post by dotNet_girl on 2010-09-28
Yeah - sorry that's what I meant. 
Thanks for the reply.  This makes sense that it would log openerp out, but after a 'killall' I'm still getting the exact same msg...

---

### Post by jwbrase on 2010-09-28
Hmmm... You might have a process run by another user (likely yourself or root, I figure) that's respawning those processes when you kill them.

Try this:

```
killall -I -r openerp.
```

This should kill all processes (without case-sensitivity) whose names begin with "openerp". Follow it up with the killall line for all processes belonging to user "openerp" (in case there's an openerp process whose name doesn't begin with "openerp"), then try uninstalling.

Now, I'm not familiar with openerp, and there may be a simpler way of doing all this for those who are...

---

### Post by dotNet_girl on 2010-09-29
Thanks for that suggestion - but still not working...

---

### Post by jwbrase on 2010-09-29
Hmmm. This is a tough nut to crack. Does anyone else have any suggestions?

If all else fails you can, at your own risk, try:

```
sudo userdel -f openerp
```

and then try uninstalling again.

That will force the removal of user openerp, even if still logged in. I don't know, however, how apt-get will react when it finds it is trying to remove a user that has already been removed, and the userdel man page says that the use of the -f option is risky, so you should probably only use it if you absolutely can't find any other solution. (It will also force the deletion of the user's home directory, and I don't know what that is for user openerp. If it's not a directory that was created by the install, using -f to remove the user could remove a folder other programs might be looking for).

---

### Post by TGBaker on 2010-12-16
This worked for me. Thanks!!!

> **jwbrase said:**
> Hmmm. This is a tough nut to crack. Does anyone else have any suggestions?

If all else fails you can, at your own risk, try:

```
sudo userdel -f openerp
```

and then try uninstalling again.

That will force the removal of user openerp, even if still logged in. I don't know, however, how apt-get will react when it finds it is trying to remove a user that has already been removed, and the userdel man page says that the use of the -f option is risky, so you should probably only use it if you absolutely can't find any other solution. (It will also force the deletion of the user's home directory, and I don't know what that is for user openerp. If it's not a directory that was created by the install, using -f to remove the user could remove a folder other programs might be looking for).

---

### Post by djtarki on 2011-09-27
> **jwbrase said:**
> Hmmm. This is a tough nut to crack. Does anyone else have any suggestions?

If all else fails you can, at your own risk, try:

```
sudo userdel -f openerp
```and then try uninstalling again.

Thanks that worked!

---

