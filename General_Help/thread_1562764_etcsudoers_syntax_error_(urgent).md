---
title: "/etc/sudoers: syntax error (urgent)"
date: 2010-08-28
forum: General Help
---

### Post by mahmoodn on 2010-08-28
I changed sudoers based on [Running shell script during startup]("http://ubuntuforums.org/showpost.php?p=3768173&postcount=7") However I can not sudo anymore:
```
mahmood@localhost:Documents$ sudo ./filename
>>> /etc/sudoers: syntax error near line 19 <<<
sudo: parse error in /etc/sudoers near line 19
sudo: no valid sudoers sources found, quitting
```
and
```
mahmood@localhost:Documents$ sudo visudo
>>> /etc/sudoers: syntax error near line 19 <<<
sudo: parse error in /etc/sudoers near line 19
sudo: no valid sudoers sources found, quitting
```

Really need your help because I can not run privileged commands.:(

---

### Post by lmarmisa on 2010-08-28
I copy here the contents of my file /etc/sudoers:

```


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```If you are not able to gain root privileges for fixing your sudoers file, I recommend you to use an Ubuntu Live CD for booting your system and then you will be able to repair the file.

Best regards,

Luis

---

### Post by mahmoodn on 2010-08-28
You mean I have delete my file and copy/paste the content (you provided)? Then what about file permisions? 777 or something else?

---

### Post by lmarmisa on 2010-08-28
Yes, but do not delete your sudoers file, simply rename it

> 
sudo mv /etc/sudoers /etc/sudoers.old
and then try to copy my sudoers file. But you will need the root privileges for doing those changes and this is a problem because sudo command is not operative.

I believe you will need to boot your system from a Live CD and then to mount the Linux partition of your hard drive. In these conditions, the changes will be possible.

NOTE: You have to modify the ./etc/sudoers file of the Linux hard drive partition mounted, not the /etc/sudoers of the Live CD system. So, be carefull locating the file to modify.

---

### Post by WorMzy on 2010-08-28
Did you use visudo to edit sudoers? Because it's supposed to prevent this sort of problem. If visudo left you with an unusable sudoers file, then you should file a bug report at launchpad to let the maintainers know.

---

### Post by lmarmisa on 2010-08-28
Sorry. I wrote this message by a mistake.

---

### Post by mahmoodn on 2010-08-28
> **WorMzy said:**
> Did you use visudo to edit sudoers? Because it's supposed to prevent this sort of problem. 
Yes. It also strange for me because as I search, people say that it can be edited with visudo. I don't know what is wrong with mine. Maybe I report a bug. Thanks for your note.

> Sorry. I wrote this message by a mistake. 
Why? I think your post was useful. I will try.

---

### Post by lmarmisa on 2010-08-28
> **mahmoodn said:**
> 

Why? I think your post was useful. I will try.

My comment was not referred to my previous messages. Simply I wrote an answer for another thread but I sent it to this conversation :confused:. I tried to delete my wrong message but it seems that this is not possible. So, I edited the message writting my apologies.

---

### Post by nerdy_kid on 2010-08-28
you don't need to boot from a Live CD; just reboot Ubuntu in recovery mode (hit shift just before the ubuntu logo).  Then select root prompt and you can edit the file.

---

### Post by mahmoodn on 2010-08-28
Thanks, with live cd it is now fixed

---

### Post by EdwardBeckett on 2012-06-10
You didn't need to get a live CD for this ... 

su - 
enter password
cd /root 
#vim sudoers
#>> fix problem
#exit
$ sudo cat /etc/sudoers

done

---

### Post by oldos2er on 2012-06-10
Please don't bump old threads.

---

