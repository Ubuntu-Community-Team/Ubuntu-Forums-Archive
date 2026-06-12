---
title: "sudo password not working"
date: 2012-02-11
forum: General Help
---

### Post by fidelandche on 2012-02-11
Hi all,

I have just spent an hour trying to search for an answer but failed, so here is the problem. I am running 11.10 as the only OS, I recently installed VirtualBox from their site and after a bit of playing with another OS, I have decided to remove Virtualbox. So I open the terminal and type the following code ```
sudo /VirtualBox.run uninstall
``` I then hit enter and type in my sudo password which I have not changed, I then get sorry please try again, I do this three times before I have to renter the code and the sudo password is not recognised. So how do I go about sorting this little problem out?

Cheers

---

### Post by The Phone on 2012-02-11
> **fidelandche said:**
> Hi all,

I have just spent an hour trying to search for an answer but failed, so here is the problem. I am running 11.10 as the only OS, I recently installed VirtualBox from their site and after a bit of playing with another OS, I have decided to remove Virtualbox. So I open the terminal and type the following code ```
sudo /VirtualBox.run uninstall
``` I then hit enter and type in my sudo password which I have not changed, I then get sorry please try again, I do this three times before I have to renter the code and the sudo password is not recognised. So how do I go about sorting this little problem out?

Cheers

Capslock?
Numlock?

---

### Post by WorMzy on 2012-02-11
What is the output of

```
sudo -l
```

---

### Post by fidelandche on 2012-02-11
No to both Capslock and Number lock,

Here is the output from sudo -1


andyandmillie@andyandmillie-Satellite-L300:~$ sudo -1
sudo: invalid option -- '1'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
andyandmillie@andyandmillie-Satellite-L300:~$

---

### Post by winh8r on 2012-02-11
The answer is here:

[http://ubuntuforums.org/archive/index.php/t-819460.html]("http://ubuntuforums.org/archive/index.php/t-819460.html")



Hope this helps.

---

### Post by WorMzy on 2012-02-11
> **fidelandche said:**
> No to both Capslock and Number lock,

Here is the output from sudo -1


andyandmillie@andyandmillie-Satellite-L300:~$ sudo -1
sudo: invalid option -- '1'
usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-g groupname|#gid] [-p prompt] [-u user name|#uid]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U user name] [-u
            user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid] file ...
andyandmillie@andyandmillie-Satellite-L300:~$

*sigh*
Try a lowercase L, not a one.

---

### Post by fidelandche on 2012-02-12
I get "sorry, try again"

---

### Post by The Phone on 2012-02-13
> **fidelandche said:**
> I get "sorry, try again"


See if you can change the password on the system?
Reinstall your OS?

---

### Post by winh8r on 2012-02-13
Try running as root

sudo su

then type 


./VirtualBox.run uninstall /opt/VirtualBox



> **The Phone said:**
> See if you can change the password on the system?
Reinstall your OS? I think a complete reinstall is a bit of a severe option for this problem!!!

---

### Post by WorMzy on 2012-02-13
> **fidelandche said:**
> I get "sorry, try again"

Then unless Ubuntu's version of sudo is different to the one I'm using, you have a serious problem. That command shouldn't even ask you for your password, it should just list your sudoers rights and associated Defaults.

e.g.
```
wormzy@sakura[pts/0]:~$ sudo -l
Matching Defaults entries for wormzy on this host:
    timestamp_timeout=0, editor=/usr/bin/vim\:/usr/bin/vi\:/usr/bin/nano, rootpw

User wormzy may run the following commands on this host:
    (ALL) ALL

```

Can anyone confirm that this happens for them?

Also, OP, can you double check that your sudo executable is located at /usr/bin/sudo, has the right permissions, and isn't a symlink to some other sudo executable or something bizarre:
```
ls -l $(which sudo)
```
e.g.
```
wormzy@sakura[pts/0]:~$ ls -l $(which sudo)
---s--x--x 2 root root 76430 Feb  2 06:51 /usr/bin/sudo

```

---

### Post by fidelandche on 2012-02-13
WorMzy - this the output andyandmillie@andyandmillie-Satellite-L300:~$ sudo su
[sudo] password for andyandmillie: 
Sorry, try again.
[sudo] password for andyandmillie: 
Sorry, try again.
[sudo] password for andyandmillie: 
Sorry, try again.
sudo: 3 incorrect password attempts
andyandmillie@andyandmillie-Satellite-L300:~$ ls -l $(which sudo)
-rwsr-xr-x 2 root root 156824 2011-09-11 20:06 /usr/bin/sudo
andyandmillie@andyandmillie-Satellite-L300:~$

---

### Post by winh8r on 2012-02-13
retracted post

cross posting

---

### Post by WorMzy on 2012-02-13
> **fidelandche said:**
> WorMzy - this the output andyandmillie@andyandmillie-Satellite-L300:~$ sudo su
[sudo] password for andyandmillie: 
Sorry, try again.
[sudo] password for andyandmillie: 
Sorry, try again.
[sudo] password for andyandmillie: 
Sorry, try again.
sudo: 3 incorrect password attempts
andyandmillie@andyandmillie-Satellite-L300:~$ ls -l $(which sudo)
-rwsr-xr-x 2 root root 156824 2011-09-11 20:06 /usr/bin/sudo
andyandmillie@andyandmillie-Satellite-L300:~$

I didn't ask you to run sudo su, but that ls output looks okay (at least it corresponds with my one remaining Ubuntu installation's ls output for the same file).

Can you change your password to something else and see if that temporarily solves the problem?

---

### Post by fidelandche on 2012-02-14
Funny the password has now started working, however using all the code supplied on the oracle site, I am unable to remove virtual box. Here is the output from the terminal


andyandmillie@andyandmillie-Satellite-L300:~$ sudo /VirtualBox.run uninstall
[sudo] password for andyandmillie: 
sudo: /VirtualBox.run: command not found
andyandmillie@andyandmillie-Satellite-L300:~$

---

