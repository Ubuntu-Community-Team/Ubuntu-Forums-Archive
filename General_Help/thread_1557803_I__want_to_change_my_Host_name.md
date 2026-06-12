---
title: "I  want to change my Host name"
date: 2010-08-21
forum: General Help
---

### Post by Hymer E 650 on 2010-08-21
Hi,
 

 I am a Ubunto newbie running Karmic Koala  9.10 and want to change  my Host name.
 

 I've read some posts on the forum but the ones I can find seem to refer to earlier version and the suggestions given don't work for me.  
 

 I'm not too wonderful with Terminal ( but can manage with guidance ) and would like to use a GUI fix if possible, can anyone help please.
 

 Many thanks

---

### Post by McNils on 2010-08-21
I found this [http://lnxg.wordpress.com/2010/04/24/living-with-lucid-setchange-host-name-graphically/](http://lnxg.wordpress.com/2010/04/24/living-with-lucid-setchange-host-name-graphically/)

---

### Post by Ginsu543 on 2010-08-21
If you want to do it using Terminal, change your host name in the following two files using sudo gedit: 1) /etc/hostname and 2) /etc/hosts. You have to change both so that you don't run into permission problems using your password as root.

---

### Post by Hymer E 650 on 2010-08-22
Hi,
 

 Thank you both for the info
 

 Firstly to McNils
 

 This looks really simple, is it an Ubunto approved way of doing it? Are there any potential probs with that way
 

 

 Secondly to Ginsu 543
 

 Now you can see just how much of a newbie I am... what I don't understand is the step by step process of editing with terminal as is what do I type in at each step?
 

 

 I do apologize for my lack of knowledge

---

### Post by Hymer E 650 on 2010-08-22
Hi,

Re the terminal method what happens at each step, how do these files appear. Do I have to save anything after and how/where do I do that??

Once again many thanks

---

### Post by dino99 on 2010-08-22
to make changes into these files, into a terminal run:

sudo gedit /etc/hostname

then change your host name then save and exit

do the same with the other file /etc/hosts

that it

---

### Post by slooksterpsv on 2010-08-22
Wouldn't:
```

sudo hostname *new_host_name*

```
work as well?

EDIT: Nope, it changes it, but everywhere else still has the old hostname.

---

### Post by philinux on 2010-08-22
> **dino99 said:**
> to make changes into these files, into a terminal run:

**sudo gedit **/etc/hostname

then change your host name then save and exit

do the same with the other file /etc/hosts

that it

That should be...
**gksudo gedit.....**

---

### Post by inameiname on 2010-08-22
Here is what I found, which seems to work:

```

To Change Computer Name:

    sudo gedit /etc/hostname
    sudo gedit /etc/hosts

    Change the name of your system in both and reboot.


To Change User Login Name:

    sudo gedit /etc/passwd
    sudo gedit /etc/shadow
    sudo gedit /etc/group
    sudo gedit /etc/gshadow

    Change the following in all four and reboot:

        In '/etc/passwd' change this line: 'me' with '(your username)'; 'Me' with '(your username)'; '/home/me' with '/home/(your username)'&#65279;:

        me:x:1000:1000:Me,,,:/home/me:/bin/bash

            - remember to cut and paste all of '/home/me' contents into '/home/(your username)' (including hidden files and folders)
            - and 'sudo chown -R (your username) /home/(your username)'

        In '/etc/shadow' change this line: 'me' with '(your username)':

        me:$6$J8VZtbBb$HDldhHGS5gOlYQB1LXJIL5P51h1ggEWlLq6swTuIIIk.iJrUTFmO9SD0Hzsj23p3/EtgbV6.oyH8/NZ9lShai0:14829:0:99999:7:::

        In '/etc/group' change these lines: 'me' with '(your username)':

        adm:x:4:me
        dialout:x:20:me
        cdrom:x:24:me
        plugdev:x:46:me
        lpadmin:x:105:me
        admin:x:119:me
        me:x:1000:
        sambashare:x:122:me

        In '/etc/gshadow' change these lines: 'me' with '(your username)':

        adm:*::me
        dialout:*::me
        cdrom:*::me
        plugdev:*::me
        lpadmin:!::me
        admin:!::me
        me:!::
        sambashare:!::me

Basically change all 'me''s in those files (may be more than the ones I mention here, I don't know for sure) to '(your username)' and you are golden.

```

---

### Post by grandsatrap on 2010-08-22
Here are all of the places that I've found that I need to change when I change my hostname:


a) /etc/hostname

b) You'll also want to edit /etc/hosts
127.0.0.1 localhost hostname
127.0.1.1 hostname
run /etc/init.d/hostname.sh and reboot.


c) change /etc/mailname to the new name.

d) Also: grep /etc looking for old name XXXXX
sudo grep XXXX `find /etc -print`

e) also change it in these places:
/etc/motd
aliases.db
postfix/main.cf

---

### Post by Hymer E 650 on 2010-08-24
Hi,

> **dino99 said:**
> to make changes into these files, into a terminal run:

sudo gedit /etc/hostname

then change your host name then save and exit

do the same with the other file /etc/hosts

that it

This worked for me.
Some of the other files suggested didn't have the host name in them and it all seems to work

Many thanks to all  of you

---

