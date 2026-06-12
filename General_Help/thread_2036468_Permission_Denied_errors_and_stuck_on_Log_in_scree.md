---
title: "Permission Denied errors and stuck on Log in screen 12.04"
date: 2012-08-02
forum: General Help
---

### Post by itagomo on 2012-08-02
Let me explain first somethings I made before having this problem:

i'm trying to run tor & vidalia but keep getting that only debian-tor user can access it and after googling, I found out some codes and run it:

note:
/var/run/tor is a directory

```
sudo mkdir -p /var/run/tor
sudo chown debian-tor:debian-tor /var/run/tor
sudo chown 02750 /var/run/tor
```restarted vidalia (which is the GUI for tor .. if you don't know tor, it's a program to communicate anonymously on the Internet..)

but same error that my desktop username can't access tor, only debian-tor user.

i issued some commands again:

```
sudo chown itagomo:itagomo /var/run/tor
sudo chmod 700 /var/run/tor
```but same error again.
I run these codes:

```
sudo chown root:root /var/run/tor
sudo chown itagomo:itagomo /var/run/tor
```and with the last code, I got an error saying "permission denied" even I have 'sudo' .. so I was thinking, maybe this was a bug then I rebooted system. And now, I'm stuck on the Log In screen after entering my password, it just says," Logging In..."

some threads say restart lightdm in the fullscreen console (CTRL + ALT + F1) .. i did so but nothing happened .. i tried doing some 'sudo' commands , but still keep getting:

```
-bash: /usr/bin/python : permission denied
```whenever I log on to the fullscreen console with my username, error always show:

```
-bash : group : command not found
```which is before
```
itagomo@ubuntu:~$ 
```.. don't know what to do here .. I think root priveleges for my username 'itagomo' was gone .. so do I need to add it back? how? 

please add any solutions that might help. thanks !

---

### Post by itagomo on 2012-08-02
hi guys .. i really need to fix this issue ... i'm stuck here in Windows .. :(

---

### Post by itagomo on 2012-08-02
bump ..

---

### Post by itagomo on 2012-08-02
bump ..

---

### Post by itagomo on 2012-08-03
bump # 3...

---

### Post by steeldriver on 2012-08-03
> **itagomo said:**
> 
some threads say restart lightdm in the fullscreen console (CTRL + ALT + F1) .. i did so but nothing happened .. i tried doing some 'sudo' commands , but still keep getting:

```
-bash: /usr/bin/python : permission denied
```whenever I log on to the fullscreen console with my username, error always show:

```
-bash : group : command not found
```which is before
```
itagomo@ubuntu:~$ 
```

It sounds like something is messed up in your .profile / .bashrc and maybe also your group memberships - it's likely fixable, but tbh you may find it easier to just create a new user account and start over

I don't know anything about tor but my guess is you should just have added your user account to the debian-tor group rather than messing with the directory ownerships - you will probably need to reinstall tor / vidalia as well to fix that

---

### Post by itagomo on 2012-08-03
> **steeldriver said:**
> It sounds like something is messed up in  your .profile / .bashrc and maybe also your group memberships - it's  likely fixable, but tbh you may find it easier to just create a new user  account and start over

I don't know anything about tor but my guess is you should just have  added your user account to the debian-tor group rather than messing with  the directory ownerships - you will probably need to reinstall tor /  vidalia as well to fix that

haha .. someone i'm waiting all over .. thank you steeldriver .. i  already tried creating a new user but still getting same errors:

```
-bash: /usr/bin/python : permission denied
-bash : group : command not found 
```what do I need to do in my  .profile or .bashrc? how about the fix for group memberships? if you  don't mind, can you add some link related to the solution ? big thanks  ..

---

### Post by steeldriver on 2012-08-03
well this is above my paygrade but I would think that if both old AND newly created users are seeing

```
-bash: 
```errors during login, that would indicate something wrong right up at the login shell level e.g. /etc/profile or /etc/environment missing / not readable / corrupted 

Or possibly it's pam-related - in which case it's WAY above my paygrade

---

### Post by itagomo on 2012-08-03
> **steeldriver said:**
> well this is above my paygrade but I would think that if both old AND newly created users are seeing

```
-bash: 
```errors during login, that would indicate something wrong right up at the login shell level e.g. /etc/profile or /etc/environment missing / not readable / corrupted 

Or possibly it's pam-related - in which case it's WAY above my paygrade

right, got it.  but anything that you can add here .. i see that /etc/profile or even /etc/environment are available and owner root has read-write access but group root & others are read only .. i added my username to root group but same problem ..

can you also check if something is wrong here, i entered this:

```
id itagomo
```result:

```
uid=1000(itagomo) gid=1000(itagomo) groups=1000(itagomo),0(root),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),128(debian-tor),111(lightdm)
```while 

```
id root
```result:

```
uid=0(root) gid=1000(itagomo) groups=1000(itagomo),27(sudo)
```isn't that root must have "root" as it's main group? 
really big thanks if you can share something..

---

### Post by steeldriver on 2012-08-03
That looks pretty messed up to me - here are my permissions as on a fairly clean VM:

```
steeldriver@desk01-vm:~$ id
uid=1001(steeldriver) gid=1001(steeldriver) groups=1001(steeldriver),4(adm),27(sudo),109(lpadmin),124(sambashare)
steeldriver@desk01-vm:~$
steeldriver@desk01-vm:~$ sudo id root
[sudo] password for steeldriver: 
uid=0(root) gid=0(root) groups=0(root)
steeldriver@desk01-vm:~$ 
```IMO you should NOT have added yourself to root's private group (0) - that's just a recipe for more weirdness / confusion - when you're in a hole STOP DIGGING :D

---

### Post by itagomo on 2012-08-04
big thanks for steeldriver. i've solved this by reinstalling 12.04. sad face .. haha ..

---

