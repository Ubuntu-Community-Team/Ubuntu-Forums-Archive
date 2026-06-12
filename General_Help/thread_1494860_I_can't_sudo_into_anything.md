---
title: "I can't sudo into anything"
date: 2010-05-27
forum: General Help
---

### Post by Yum_Salad on 2010-05-27
Hi there

So basically, I can su to root just fine. sudo in the gui and in the terminal cause errors.

sudoers content
```
# /etc/sudoers
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
```


/etc/groups admin excerpt
```
admin:x:123:user
```

Also, in the system > admin > users and groups menu, "user" has admin privileges.

What is going on here?

---

### Post by ibuclaw on 2010-05-27
Specifying what type of errors you are getting may help...

Usually the #1 reason for sudo not working is a bad dns lookup.

---

### Post by Yum_Salad on 2010-05-27
I get popup alerts saying that i don't have the privileges. that's it.

Also, i logged into root and created another user via the shell and gave this user a password. I then logged out via the gui and tried to log into this newly created user but i got 3 popup errors.

Popup messages:
1. "Could not update ICEAuthority file /home/devuser/.ICEAuthority 
2. There is a problem with the configuation server. g-conf sanity check. satus 256
3. 3rd said nautilus failed to create the folders for this user. /Desktop and .nautilus .

This sounds like catastrophe. I've been using ubuntu for 4 years and i've never seen such craziness!

:confused:

---

### Post by ibuclaw on 2010-05-27
> **Yum_Salad said:**
> 
This sounds like catastrophe. I've been using ubuntu for 4 years and i've never seen such craziness!

:confused:

;)


What is the output of:
```
id
```
And:
```
ls -ld ~
```

---

### Post by Yum_Salad on 2010-05-27
```
user@desktop:~$ id
uid=1000(user) gid=1000(user) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(fuse),105(lpadmin),112(netdev),119(admin),1000(user)


>> Included the output for root
uid=0(root) gid=0(root) groups=0(root)

```

---

### Post by sisco311 on 2010-05-27
never mind

---

### Post by ibuclaw on 2010-05-27
You seem to have two conflicting pieces.

1)
> **Yum_Salad said:**
> 
/etc/groups admin excerpt
```
admin:x:[COLOR="Red"]**123**[/COLOR]:user
```

Also, in the system > admin > users and groups menu, "user" has admin privileges.


2)
> **Yum_Salad said:**
> ```
user@desktop:~$ id
uid=1000(user) gid=1000(user) groups=(...),[COLOR="red"]**119**[/COLOR](admin),1000(user)

```

I'd double-check /etc/group again if I were you...
```
grep "admin" /etc/group
```
If proven to have more than one value, you'll have to correct it in recovery mode.


And can you also post the output of:
```
ls -ld ~
```

---

### Post by mhgsys on 2010-05-27
Btw, not really my cup of tea ... (though I messed enough with the sudoers file to get locked out once..lol_)

This is my /etc/sudoers file.

```
# /etc/sudoers
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

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

notice the difference between your file and mine.

**yours;**

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# **%sudo ALL=NOPASSWD: ALL**

**mine**

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
**%sudo ALL=(ALL) ALL**

---

### Post by dabeej on 2010-05-27
In a terminal do a sudo -s.

What does it give you?

What are you running under sudo. Some application require a little more to it than just putting sudo it front of it.

---

### Post by ibuclaw on 2010-05-27
> **mhgsys said:**
> 
notice the difference between your file and mine.

Just one flaw in your plan though. He is not part of the sudo group, and he need not be either. ;)

---

### Post by mhgsys on 2010-05-27
My plan?
I've got plans?

Sure this is the standard /etc/sudoers file.

I've never edited that file on this machine..

and again; this is not my cup of tea.. I was only comparing the file.

---

### Post by ibuclaw on 2010-05-27
> **mhgsys said:**
> My plan?
I've got plans?

Sure this is the standard /etc/sudoers file.

I've never edited that file on this machine..

and again; this is not my cup of tea.. I was only comparing the file.

Of course, nothing wrong with your observations. So long as you used.
```
sudo visudo
```
To have a look at your sudoers file, you're all in the green. :P

---

### Post by mhgsys on 2010-05-27
Actually I used 
```
 sudo visudo -s
```

does that make me even greener?

---

### Post by Yum_Salad on 2010-05-28
Requested info!

```
sudo -s
user is not in the sudoers file.  This incident will be reported.
```


```
user@desktop:~$ ls -ld ~
drwxr-xr-x 28 user user 4096 May 28 04:57 /home/user
```


```
user@desktop:~$ grep "admin" /etc/group
lpadmin:x:105:user
admin:x:119:user
```

---

### Post by ibuclaw on 2010-05-29
> **Yum_Salad said:**
> Requested info!


OK, still nothing out of the normal.

Next, can you run:
```
sudo -l
```
And post the output.


Regards
Iain

---

