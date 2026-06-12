---
title: "authentication"
date: 2012-05-14
forum: General Help
---

### Post by gh0sthead on 2012-05-14
Hi people

As many others I am new on ubuntu and now Ive got a serious problem. Im stuck. 

When I want to install something or even just change something I am asked for authentication. I type my password in- but it doesnt work. I know my password very well and I have already changed it in the boot mode. It didnt work again. I can log in into my account- i am the only user -but I just cant get access to download something! That is really annoying.

I was already lookin for some help on google because I know that most things one can just read online in other forums but I didnt found anything on this subject. Now I registered here to get help and I really hope you guys could help me with that problem.

---

### Post by d.atanasov on 2012-05-14
Hi and welcome to Ubuntu Forums. 
Can you describe in details what is your problem. Can you provide some information about the ubuntu you have. Perhaps you could give some output of some command in Terminal which wont work ?

---

### Post by QIII on 2012-05-14
If I ask you to install something fairly common, could you copy back the exact text of what you see in the terminal?  (Highlight the text and press control+shift+c)

```
sudo apt-get install htop
```

htop is a command line system monitoring tool and is safe to install.

---

### Post by gh0sthead on 2012-05-14
Ive got the latest version of ubuntu means 12.04 lts. my problem is that i cant get the administrator right because i always get authentication failure when hit enter after entering the password i use to log in to my user account.

---

### Post by gh0sthead on 2012-05-14
I typed in the command you wrote then I received the message to type in my password. I tried the one I use to log into my account. It didnt work...

mario@ubuntu:~$ sudo apt-get install htop
[sudo] password for mario: 
Sorry, try again.
[sudo] password for mario: 
Sorry, try again.
[sudo] password for mario:

---

### Post by d.atanasov on 2012-05-14
Let`s us change the root password again. Perhaps you lost root access. Here is some example 
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrativeroot-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrativeroot-password)

---

### Post by steeldriver on 2012-05-14
it sounds like either:-

o you are using a different account from the primary one created during the install (iirc subsequently created accounts don't get sudo access by default)

o your sudoers configuration got modified 

first thing to check is what group memberships your account has

```
$ groups
```For 12.04 you need to be in group 'sudo' I believe (was 'admin' in prior releases)

---

### Post by gh0sthead on 2012-05-14
I am not using a different account- of this I am sure.

I checked it- and got this:

o@ubuntu:~$ groups
mario adm cdrom sudo dip plugdev lpadmin nopasswdlogin sambashare
mario@ubuntu:~$

---

### Post by gh0sthead on 2012-05-14
ill try it

---

### Post by gh0sthead on 2012-05-14
> **d.atanasov said:**
> Let`s us change the root password again. Perhaps you lost root access. Here is some example 
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrativeroot-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrativeroot-password)

This I already tried several times before I even registered here- it didnt work

---

### Post by steeldriver on 2012-05-14
OK so your account *is* a member of group 'sudo'

First you could check to see if there's anything in /etc/sudoers.d/ that might be breaking things (i.e. denying based on UID/GID/host or whatever). By default there's nothing except a README file there iirc.

Next thing to check is that group 'sudo' actually has sudo privileges - you will need to log in as root and then use visudo to make sure that your sudoers file contains the line

```
%sudo   ALL=(ALL:ALL) ALL
```It's also important that there are no *subsequent* lines that might override that - the default file only has entries for root, %admin and %sudo I think.

EDIT: one more thing (please don't take this the wrong way) - you are typing your user (mario) password, not the root password, right?

---

