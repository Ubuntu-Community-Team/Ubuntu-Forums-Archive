---
title: "Samba Problemo :-("
date: 2006-06-21
forum: General Help
---

### Post by tikig on 2006-06-21
I have looked at the ubuntuguide.org/wiki/Dapper#How_to for Samba Networking

Somehow I've failed so far to get it to work. I have two problems.

I have a XP Pro and a Dapper Box with static IP's. 

Problem #1:
Ubuntu can see and access the XP Pro box. It cannot access all files some large Ghost images it comes back and says "Error while copying. "smb://mjo-...e1001.GHS" cannot be copied because you do not have permissions to read it." To my knowledge it's just like every other file in that folder that it can copy. If from the Ubuntu box I check the permissions of that folder is says it's 755. The size of that folder is 5 items, totalling 8.3GB

Problem #2: XP Pro box can see the Ubuntu box but I always get "The network path was not found." error.

If in explorer I put in \\nameofUbuntucomputer I get cannot find check spelling. If I put in the IP address I get a username and password box. When I put in my Samba username and password it doesn't work.

My testparm is below.

[global]
        workgroup = TIKIG2
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* 
%n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[public]
        comment = Public Folder
        path = /home/public
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0777
        directory mask = 0777
        guest ok = Yes 

I have already created a Samba user and additional computer user.

Any suggestions. I've looked at the Wiki's. I'm a noob on Ubuntu, MCP in Windows.

-Tikig

---

### Post by tikig on 2006-06-22
Re: Problem #1 the files that I am not able to copy actually have a folder permission state of 755 and a file permission state of 744. The other Ghost images I can copy have the same permission setup.

Is SMB sharing broken somehow or not working consistently in Ubuntu?

Re: Problem #2 I still have made no progress and am considering uninstalling from the Synaptic Package Manage. The Linux community needs to recognize that file sharing needs to be accomplished in an easy manner. Samba in it's current form just doesn't provide a user friendly way to accomplish file sharing easily. I'm a noob to linux but even a noob in windows can get a workgroup setup in 15 minutes. I hope the Ubuntu community sees the number of Samba related posts and understands the importance that this topic has if Linux (ubuntu) is ever going to make it mainstream.

-tikig

---

### Post by scxtt on 2006-06-22
have you tried:
[indent]\\NameOfUbuntuComputer\public[/indent]
from a windows "map network drive"?

---

### Post by Stormbringer on 2006-06-23
The problem you described in your first post (samba setup, name resolution) isn't the fault of Ubuntu ...

Re: Samba Setup
In the first place you should understand that Samba isn't a simple "Filesharing" daemon speaking the "Windows Filesharing Protocol" (to keep it simple) - it's a full blown server solution that can be configured as far as to resemble an Windows 2000 Primary Domain Controller.

Re: not easy to configure
THERE IS a graphical frontend to configure samba: SWAT (Samba Web Administration Tool)
It's included in the repositories and can be installed at anytime by typing "sudo apt-get install swat" inside a terminal.
However, this won't save you the trouble to know what you are doing.

Re: Doesn't find my computer by name but by IP instead
As you most likely don't run a local DNS-server for your LAN, and no WINS in samba, it's no wonder that name-lookups are doomed to fail.


Let's move on to your problem and it's possible solution...

First, let us stop samba - open a terminal and type:

sudo /etc/init.d/samba stop

Now, here's a smb.conf I adopted from the sample output you posted in your first post ... should get you on track. Edit yours to match with the configuration below.

sudo gedit /etc/samba/smb.conf

```

[global]
    ; General server settings
    netbios name = TIKIG
    server string =
    workgroup = TIKIG2
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; If you need access to the home directories uncomment the lines below
; and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; Only needed if you run samba as a primary domain controller. Not needed
; as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; Again - only needed if you're running a primary domain controller
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom0
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Public]
    path = /home/public/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = nobody
    force group = nogroup

```

Since you are sharing the contents of "public" with other users you should set the permissions of the folder to 777.

sudo chmod 0777 /home/public

Time to start samba again ...

sudo /etc/init.d/samba start

Time to add yourself as a user to samba ...

sudo smbpasswd -L -a tikig
sudo smbpasswd -L -e tikig

Now - all the other users who should have access to the share need a valid login.

sudo useradd -s /bin/true username
sudo smbpasswd -L -a username
sudo smbpasswd -L -e username

Note:
- Substitute "username" with the real username - DON'T USE SPACES!
- Since the users don't need access to the commandline shell it's a good idea to use /bin/true as their "shell".
- Repeat the step above until all user-accounts are created.

So much for samba --- now you need to tell Windows that there's a WINS server inside the network to do IP-to-Name resolution.

Boot you Windows box ...

- Click "START" -> "Control Panel"
- Double-Click "Network Connections"
- Find your Network card.
- Right-click the icon and select "Properties"
- Select the "TCP/IP" protocol and click the "Properties" button.
- 3rd Tab - add the IP address of your Ubuntu box (I hope you don't use a dynamic dhcp lease) to the WINS server list.
- Click "OK"
- Close everything.
- Reboot Windows

Upon reboot you should be able to use Netbios-names (i.e. net use z: \\TIKIG\public) inside of Windows (as long as your Linux box is up).

In case you have any further question feel free to ask for help.

Cheers, Storm

---

### Post by beerorkid on 2006-06-23
holy crap storm

quite a nice little howto you done did put up there.

I have been messing with a samba share for about a week now.  I have it working pretty good, but now I can add a few more things to it.

one question:
```
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
```
is that to speed up samba?  I heard that samba is a little slow and you can get in there and speed it up a little.

Thanks.

EDIT: searched around and sho nuff, that is supposed to kick it up a notch.

---

### Post by Stormbringer on 2006-06-23
Thanks for your cheers, Beerorkid.

However, this was just a "quick-and-dirty" reply to tikig - the config is a trimmed-down version of the smb.conf I use on my PDC.

As for your question:

For me it provided a little speed-up ...
I'm on GbE (non-Jumboframes as I have 100Mbps devices in the network); transfers went from ~28-32MB/s up to 39-43MB/s.

It's safe to give it a try if you like since it won't hurt anything.

Storm.

---

### Post by ayoli on 2006-06-23
hey Stormbringer, thx fot nice tip about socket options ;)
didnt know that.
cheers.

---

### Post by Stormbringer on 2006-06-23
Hmm ... this almost sounds as if I should torture my innocent keyboard and write an HOWTO on the matter ("HOWTO: Setup samba peer-to-peer with Windows Workstations" and "HOWTO: Setup samba as a full-blown PDC with DHCP and DNS for your LAN").

Let's see ... if I get a minute I'll try to put something together that'll cover that topic more thouroughly (I know that there are a few HOWTOs around - but they aren't really useful as you can see).

---

### Post by Arisna on 2006-06-23
That would be great, Stormbringer--I have personally struggled with Samba on both Gentoo and Ubuntu before finally getting things working the way I want them, alternately using Distro-specific docs, official Samba docs, and stuff on university servers that I found on Google.

One item that I believe may be worth including (and you may have realized this already) is how to make Ubuntu behave like another Windows box on the network.  That is, able to provide shares without ever wanting a password.  This was surprisingly difficult for me.  Ended up using this kind of config:

[global]
security = share # Convenient, but not as secure as "user"

hosts deny = ALL
hosts allow = 127. 192.168.1. # Recover some security by restricting access to those on same LAN

---

This config would allow shares marked "public" to be accessible without having to enter a password on the remote machine at any point.  Should be secure enough for most home users, although I am not an expert.

---

### Post by Stormbringer on 2006-06-23
Arisna, I would suggest you to use "hosts allow" inside the shares section ... this will lead to a more fine grained security if used in conjunction with "valid users".

Examples:

```

; Really public share
[Public]
    path = /home/public/
    browseable = yes
    read only = no
    guest ok = yes
    hosts allow = 127. 192.168.1.
    create mask = 0644
    directory mask = 0755
    force user = nobody
    force group = nogroup

```

The example above allows guests (non-authenticated) to access the share (very bad idea in case you store confidential data on the share). The only restriction in place is that the workstations have to be inside the LAN (network segment of 192.168.1.0/24 ranging from 192.168.1.1-192.168.1.254).

In case you segmented your network into subnets you may use the network/subnet notation ( i.e. 192.168.1.0/8 ).

```

; Secured public share
[Public]
    path = /home/public/
    browseable = yes
    read only = no
    guest ok = no
    hosts allow = 127. 192.168.1.
    valid users = user1, user2, user3, user4
    create mask = 0644
    directory mask = 0755
    force user = nobody
    force group = nogroup

```

This is a more secured "public" share where only a set of users are allowed access. You may also simply the managment by granting access on a per-usergroup basis.

Let's assume you added all users into a usergroup called "public" - you may also write:

```

    valid users = @public

```

to grant everyone inside the "public" usergroup access to the share.


However, I'll try to write a HOWTO on the matter within the next few days ... it really seems as there's a need to discuss different setup scenarios.

---

### Post by Stormbringer on 2006-06-24
As promised I wrote the first HOWTO - I hope it's useful for you guys.

**[HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605")**

---

### Post by tikig on 2006-07-07
Stormbringer,

I was away from my computer for a few days and then tried the fix you posted. Well, simply put, you solved my problem and it took a whopping 5 minutes. (I even add the same credentials as my XP box for Samba username/password and I don't have to authenticate into the share, doubleclick and it opens.) 

I was able to copy everyfile No Problemo.

I have also looked your Samba Peer to Peer How To

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

It should become part of the master WIKI/Help on the topic. Would have potentially saved me 2 hours. (I was actually one line of code away from it working me thinks...Ugh sudo smbpasswd -L -e "username")

Have you complete your next project  - HOWTO: Setup Samba as an Primary Domain Controller with additional services 

Looking forward to it. Again Thanks for your assistance!

-tikig

---

### Post by Stormbringer on 2006-07-07
Hi, tikig!

I'm working on my second HOWTO, but progress is rather slow as I'm currently lacking the time to continue writing (this'll be the hell of a beast as the config of DHCP and DNS isn't explained that easily).

However, glad I could help you out.

Cheers,
Storm.

---

