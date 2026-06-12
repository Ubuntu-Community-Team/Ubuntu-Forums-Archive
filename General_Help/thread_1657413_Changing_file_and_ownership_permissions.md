---
title: "Changing file and ownership permissions"
date: 2011-01-01
forum: General Help
---

### Post by bk__888 on 2011-01-01
Hi,  I installed Ubuntu from the alternate cd a few days ago to save space and resources on a very old laptop. (install command line, then add what I wanted)      

But I have struck an interesting problem with file permissions.  

Various programs like synaptic, leafpad, pcman, Banshee, all require I enter the root password to execute them (or sudo command from terminal).  I want to change synaptic from root ownership to sudo and leafpad etc to execute without using the sudo command in terminal.    

I would appreciate it if I could get comments on the commands before I execute them in terminal and if I am introducing a security problem, as I am still learning bash. 

$ sudo chown sudo:sudo synaptic       

I would still be asked for my sudo password before being able to open synaptic? As in standard Ubuntu instead of root password.

 then 

$ sudo chmod 777 leafpad pcman Banshee      

All users could open these programs from the menu? I have my admin account and a general account which I use for everyday things like surfing the net and listening to music.      

I would not be introducing any security issues? (I am the only user on this computer).      

Thanks for any comment.

---

### Post by solar george on 2011-01-01
That won't work, synaptic needs to run as root user and chowning it won't make any difference. However banshee et.al. shouldn't need to be run as root unless something has been mucked up on your install, do you mean that you can't run them at all except as root or that they don't function correctly except as root?
Perhaps what you are seeing is an issue with the system groups which your main user is a member of - this might occur if you've been doing a lot of setup manually and you made a mistake somewhere.
If you've been mucking about with the permissions of system files I'd strongly advise you to re-install before you try to fix anything else.

---

### Post by bk__888 on 2011-01-02
I can't start Synaptic via the menu as it asks for the root password. The only way I have found is with sudo in terminal.

The rest ask for root password if I try to start them from menu. Unless I use sudo before the command most programs are glitchy and tend to crash.

As of yet I haven't touched any permissions. I have been busy reading man pages etc until I am sure I know what I am doing. 

I did find this interesting statement in Rootsudo on the Ubuntu community pages.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

"You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root."

I suspect this may be the problem?

An uninstall of the affected programs, then run Synaptic with the gksudo command to re-install?

Thanks for your reply.

---

### Post by solar george on 2011-01-02
That wouldn't explain the glitchyness, as for the root password question IIRC you'll need to configure the launchers to use gksudo rather than gksu (which is done by default on standard installs). I've never had problems like you're experiencing when I've built up systems from the cli.

Maybe you'd be better off re-installing with something like lubunut or xubuntu which will set all this up for you properly by default while still being not so needy in terms of resources. If the memory use of the installer is a problem try using the alternate versions of their installers and just letting it install the default system.

---

### Post by bk__888 on 2011-01-03
Thanks for your advice.

I will most likely have another try at installing from the alternative cd on the weekend. This time I wont use --without-recommends in my initial install from cli.

I will play with the system offline (I have everything backed up) during the week, just because I am becoming a little addicted to the question "Why is it so?" & "How fast can it go on this old clunker?" in Ubuntu. Heck If I break it, I still have my Ubutnu Live CD and it doesn't matter if nothing works after doing the incredibly stupid and I will do a fresh install later anyway.

I  appreciate your help very much.

---

### Post by theozzlives on 2011-01-03
Synaptic and sudo are asking for YOUR password. As administrator, you can run as root using your password. The only command I know of that needs root password is "su" which you shouldn't use anyhow.

---

### Post by solar george on 2011-01-03
I think what the OP is describing involves a mucked up install whick, amoungst other things has caused gksu(do) to be configured in su mode where it uses the gksu and asks for the root password rather than gksudo with the admin password.

---

