---
title: "Help: Can't login into Gnome....PAM gdm"
date: 2006-03-25
forum: General Help
---

### Post by intel on 2006-03-25
[B]Help! Can't login into Gnome

[/B]**Help! Can't login into Gnome**[B]....PAM gdm

My ubuntu 5.10 boots up X starts & instead of a field for login username

a window shows up and says :-

> [CENTER]*"can't find PAM configuration for gdm"*[/CENTER]
    
then i do ctrl+alt+F1 & at the login prompt I type my username & enter I get :-

> [CENTER]*"login: PAM Failure, aborting:Critical error - immediate abort"*[/CENTER]
    
Can anyone help me trouble shoot this problem .......pretty please....

looking forward to logging into my desktop.........[/B]

---

### Post by intel on 2006-03-25
**/etc/pam.conf**

> # ---------------------------------------------------------------------------#
# /etc/pam.conf                                     #
# ---------------------------------------------------------------------------#
#
# NOTE
# ----
#
# NOTE: Most program use a file under the /etc/pam.d/ directory to setup their
# PAM service modules. This file is used, but not recommended
# ---------------------------------------------------------------------------#

# Format:
# serv.    module       ctrl          module [path]    ...[args..]             #
# name    type       flag                                 #



---

### Post by intel on 2006-03-25
[B]Help: Its getting weirder!!

[/B]Ok i was trying to post the contents of /etc/pam.d/

I had booted into Knoppix CD
Mounted the file system, posted the contents of
/etc/pam.conf

next in Konquerer I clicked on /etc/pam.d/

and it FROZE up !!!

No hdd activity for like 2-3 min. so i rebooted

& tried again ....same result !!

Next i tried with Ubuntu Live CD

in Nautilus i clicked on /etc/pam.d/

and this also FROZE up again !!

Again no hdd activity

so i re-booted

Now is this some sort of security feature
that when booting from a live CD you can't
browse /etc/pam.d/ ???

What must i do...
i do not want to abandon the system

please help me restore the system.....

When i booted up the recovery mode in ubuntu's grub

I got to a root prompt what happened next is WEIRD !!

```

root@<mymachine>:~# ls -l /etc/pam.d/
[4294730:255000] double fault, gdt at c03ff880 [255 bytes]
[4294730:255000] double fault, tss at c0347080
[4294730:255000] eip = c011510e, esp = cd3fffe4
[4294730:255000] eax = cd400068, ebx = 0000000b, ecx = 0000000d, edx = 00000000
[4294730:255000] esi = 0000000e, edi = c031693b
``` 
and then it hung up again!

I had to write the above message on a piece of paper and type it !

I tried to look at the contents of pam.d in knoppix cd, Ubuntu live cd & Ubuntu recovery mode

and the result was the same

It Hung up, it FROZE

Please help me recover my system.....

---

### Post by trent dillman on 2006-03-25
Please post your system specs (especially CPU info), graphics card/driver, and any recent kernel changes.

---

### Post by intel on 2006-03-25
OK update:

Booted up into recovery mode got root prompt

did 

> fsck /dev/hdc2

came up clean no errors

Now when i do

> ls -l /etc/pam.d/

i get 0 files

How do i get the contents of pam.d to the way they were?

---

### Post by intel on 2006-03-25
**Another update**

When i boot using recovery mode of ubuntu
i get root prompt

i type 

> #startx 
i get gnome ! YAY

so i go to system> preferences> users& group

reset my normal user password

logout

reboot

then again i get the same error when gdm starts,

i think gdm wants PAM config in pam.d 

How do i remake the contents of /etc/pam.d/
which is empty now...................................

Please help me

---

### Post by intel on 2006-03-25
System hosed after following advice from

"Blissex", "redguy" and most notably "tkup"

on irc://irc.freenode.com/#ubuntu on 26-03-2006

---

### Post by trent dillman on 2006-03-25
Hosed? How so?

---

### Post by intel on 2006-03-25
Well first only had PAM issues

then tkup asked me to remove & install libpam-modules

that screwed up apt

(something about slocate.....error)

kept asking me to dpkg --configure -a

so now apt is broken too

in addition to pam.d being empty

I don't know what to do, my system is unusable now !

---

