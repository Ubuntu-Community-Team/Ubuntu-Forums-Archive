---
title: "Help setting up file Locking in Samba"
date: 2012-04-12
forum: General Help
---

### Post by TheHippy on 2012-04-12
Hi Guys,

I have looked through the search results on this forum, and on google too.

Basically I have samba file server set up and working, and have had it working for a while now, but i need to have it lock the file when its being edited by someone else.

I don't really want version control, just the file locked until its saved/closed.

I thought i had to add strict locking = yes but it doesn't seem to have done the trick, Here is a pastebin to my config: [http://pastebin.com/2KgR713n](http://pastebin.com/2KgR713n)

Any help would be really appreciated, or a point in the right direction!

Many thanks

Danny

---

### Post by Hugh Mulqueen on 2012-04-12
Sorry man I'm a bit confused by your question. Do you want to allow other people to edit the file? 

did you forget to reload samba after editing smb.conf?
[B]
service samba restart[/B]

If thats any help...

---

### Post by TheHippy on 2012-04-12
i want people to be able to edit the files, but only when they are not being edited by someone else..

i have done restart smbd as that was on the tutorial..

---

### Post by Morbius1 on 2012-04-12
I would run the following command before determining what works and what doesn't:
```
testparm -s
```When you do you will see that you have a whole mess of errors with that smb.conf.

For one: it's "oplocks = yes" not "oplock = yes"

But the biggest problem is where you put this:
     > browseable = yes
    server string = Samba Server
    guest account = pcguest
    hosts allow = 192.168.1.*
    printcap name = /etc/printcap
    load printers = yes
    printing = lprng
    log file = /var/log/samba/%m.log
    max log size = 50
    security = share
    socket options = TCP_NODELAY
    local master = no
    domain master = no
    preferred master = no
    interfaces = 192.168.1.166/24
    strict locking = yes
    oplock = yes
The location where you have it is being interpreted by samba as being part of the [print$] share. Samba reads smb.conf from [section] to [next section] so anything between them is being placed in the previous [section] which in this case in [print$]. You have a lot of stuff that belongs in the [global] section so I would put them where they belong.

One other thing. If you want to have comments in your smb.conf like this one:
> Under Share Definitions Edit the following.Put a # sign in front of the line telling Samba to ignore it otherwise it wastes time logging errors:
> [COLOR=Blue]**#**[/COLOR] Under Share Definitions Edit the following.

---

### Post by TheHippy on 2012-04-13
ah thank you, i copied a tutorial and that was the config setup they had i just changed values etc, teach me for not reading properly.

I will try this now and report back!

---

### Post by TheHippy on 2012-04-26
Ok, so i have changed those parts and it looks a bit better

```
webserver@ubuntuserv:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[public]"
Processing section "[tmp]"
Loaded services file OK.
Invalid character * in hosts allow list (192.168.1.*) for service printers.
Invalid character * in hosts allow list (192.168.1.*) for service print$.
Invalid character * in hosts allow list (192.168.1.*) for service public.
Invalid character * in hosts allow list (192.168.1.*) for service tmp.
Server role: ROLE_STANDALONE
[global]
        server string = Samba Server
        interfaces = 192.168.1.166/24
        map to guest = Bad User
        obey pam restrictions = Yes
        guest account = pcguest
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:               * %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = /etc/printcap
        local master = No
        domain master = No
        dns proxy = No
        wins support = Yes
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        comment = Home Directories
        read only = No
        create mask = 0700
        hosts allow = 192.168.1.*
        printing = lprng
        print command = lpr -r -P'%p' %s
        lpq command = lpq -P'%p'
        lprm command = lprm -P'%p' %j
        lppause command = lpc hold '%p' %j
        lpresume command = lpc release '%p' %j
        queuepause command = lpc stop '%p'
        queueresume command = lpc start '%p'
        strict locking = Yes

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes

[public]
        path = /home/pcguest
        create mask = 0777
        guest ok = Yes

[tmp]
        path = /tmp
        create mask = 0777
        guest ok = Yes

```

It says strict locking = yes but when i open a file, and then my colleague opens the same file it still opens, i dont want him to be able to open it while i have it open..

Is there anything i can do?

Many thanks

---

