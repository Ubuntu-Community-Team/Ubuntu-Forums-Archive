---
title: "changed my account from administrator to standadr by mistake !"
date: 2011-10-20
forum: General Help
---

### Post by shantiq on 2011-10-20
how do i get back to admin rights


was trying to tweek things after new upgrade to oneiric


and fiddling with user accounts i must have changed some settings


how can i claw my admin rights back


see attached image


this is what i get now

```
sudo apt-get update
[sudo] password for shantiq: 
Sorry, user shantiq is not allowed to execute '/usr/bin/apt-get update' as root on shan.
shantiq@shan:~$ 


```

---

### Post by papibe on 2011-10-20
Hi shantiq.

Could you post the result of this command:
```
groups
```
Regards.

---

### Post by sisco311 on 2011-10-20
If you didn't log out, then run:
```
sudo gpasswd -a shantiq admin
```
Otherwise follow this instructions:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by shantiq on 2011-10-20
> **papibe said:**
> Hi shantiq.

Could you post the result of this command:
```
groups
```
Regards.


```
shantiq@shan:~$ groups
shantiq adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin nopasswdlogin sambashare shantiq2
shantiq@shan:~$ 

```

---

### Post by papibe on 2011-10-20
You left yourself out the admin group (just like sisco311's suggested). Follow his instructions: try to add yourself back, or follow the tutorial in the link he provided.

As usual, very good catch sisco311!

Regards.

---

### Post by fdrake on 2011-10-20
if that doesn't work check your sodoers file as root or with a live cd:

```

less /etc/sudoers

```
maybe you have applied some specific restrictions.

---

### Post by shantiq on 2011-10-20
ok did this from the linked info


```
Do the actual repair

Case 1: If you'd removed your last admin user from the admin group, then type
adduser username admin
where username is your actual username.
```


and got


this


```
gpasswd: cannot lock/etc/group; try again later


adduser `/usr/bin/gpasswd -a shantiq admin'  return error code 1. Exiting.
```

---

### Post by goldentony111 on 2011-10-20
can you system restore

---

### Post by papibe on 2011-10-20
Looks like there are already locks (something went wrong?). Check it like this:
```
ls /etc/passwd.lock /etc/shadow.lock /etc/group.lock /etc/gshadow.lock
```
If you are in safe mode, with a root prompt (#) you can delete them:
```
rm -i /etc/passwd.lock /etc/shadow.lock /etc/group.lock /etc/gshadow.lock
```
And then try again to add yourself to the admin group.

Hope it helps,
Regards.

---

### Post by shantiq on 2011-10-20
seems it is not there

```
shantiq@shan:~$ rm -i /etc/passwd.lock /etc/shadow.lock /etc/group.lock /etc/gshadow.lock
rm: cannot remove `/etc/passwd.lock': No such file or directory
rm: cannot remove `/etc/shadow.lock': No such file or directory
rm: cannot remove `/etc/group.lock': No such file or directory
rm: cannot remove `/etc/gshadow.lock': No such file or directory
shantiq@shan:~$ 


```

---

### Post by papibe on 2011-10-20
You need to execute those commands as root, right after a safe mode boot, 
and choosing something like 'drop root prompt'. You have to have a # prompt, just like the pictures on the tutorial.

Try again, and start with the adduser command.

Tell us how it goes,
Regards.

---

### Post by shantiq on 2011-10-21
thanx for your time papibe but not there yet

ran those two commands from the  drop root prompt first the ls then the rm -i    and it tells me there is no such file



so still not there quite

maybe to show what i did to make this mess will help find a solution


i went to user accounts unlocked it and changed to automatic login  [which is what i was after]
then the accounttype drop down box opened by inadvertance and presented with the choice of admin or standard picked standard as i was not sure


this is how this started      hope it helps to find a solution :)    thanx    shan

---

### Post by shantiq on 2011-10-21
bump


anyone?   any ideas?

---

### Post by fdrake on 2011-10-21
1. the reason why you cannot use "sudo" is because you set up your account as a standard user

2. the fact that you cannot lock the /etc/group file is because is probably being use by another (gui-)program

try this (you should use visudo in this cases but i 'll make it easier for you)

1. reboot as root (or use a live cd)
2. type
```

gedit /etc/group

```
3.
look for this line:
> 
admin:x:119:user1,user2

and change it to this by adding your user name at the end(comma+username)
> 
admin:x:119:user1,user2[COLOR="Red"],shantiq[/COLOR]

4. reboot and use sudo!

ps. I am assuming that your sudo program is set to run on "admin" group. Check this file as a root:
```
gedit /etc/sudoers
```
and make sure it says admin like in this case from these lines:
> # Members of the admin group may gain root privileges
%**_[COLOR="Red"]admin[/COLOR]_** ALL=(ALL) AL

---

### Post by dmoconnell on 2011-10-21
just want to throw my 2 cents down. If you have access to the root account (if before you had changed your account status you had set a root password) then simply log into it(root) and from inside root re-change your account status.
this will only work if you have access to root but it does work (i myself accidentally standard-ized my account (woops) if anyone knows a simple way to set root account password without admin status (guess it has something to do with the terminal thats in "safe mode" (the terminal outside the GUI area (don't remember the real name of it) and could post it would be cool. (accessing root account would be a really quick way to change his account status back)
again just my 2 cents take it, leave it or use it to call a bet with :)
Dm

---

### Post by shantiq on 2011-10-22
> **fdrake said:**
> 1. the reason why you cannot use "sudo" is because you set up your account as a standard user

2. the fact that you cannot lock the /etc/group file is because is probably being use by another (gui-)program

try this (you should use visudo in this cases but i 'll make it easier for you)

1. reboot as root (or use a live cd)
2. type
```

gedit /etc/group

```
3.
look for this line:

and change it to this by adding your user name at the end(comma+username)

4. reboot and use sudo!

ps. I am assuming that your sudo program is set to run on "admin" group. Check this file as a root:
```
gedit /etc/sudoers
```
and make sure it says admin like in this case from these lines:



ok there Drake and thanx a lot for this so i went straight to drop to root shell prompt or that was my intention at least:KS


and guess what new injury


for reasons best known to itself it throws up this see image

recovery menu   **(limited read-only menu)**



and does not let me go down to the root shell prompt


so what now ?    i am a little perplexed; it let me do that before but no longer    weird

===============================================

i guess it means going the live cd route    but i do not know how to do this

i have 11.10 on a usb stick available to me      how will i use that?   step by step please    i have no knowledge in this area   thanx



you also mention a visudo route would i not need to be root for that? which is my problem here



Please carry ion helping guys i feel like i am locked outside the door right now   :KS     Grateful for all clever suggestions

---

### Post by shantiq on 2011-10-22
ok got my sudo back but had to go to my usb stick and re-install 11.10 on top of 11.10


kept all my files but knocked off all my programs


anyway back in the building as it were   


thanx for all your help     shan:KS

---

