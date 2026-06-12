---
title: "Want Windows household to Ubuntu household..."
date: 2011-04-26
forum: General Help
---

### Post by NickellossAych on 2011-04-26
Hello all,
     I have known about Ubuntu for some time now, and have been toying with it myself. I replaced my Vista OS a while ago with Ubuntu and have enjoyed it, but I am in no way keen to all of its wonderful possibilities. I come from a home of all Windows desktops/laptops (except for my Ubuntu desktop). I have been trying to convince my family to change because I  know the possibilities with Ubuntu, but here's the catch, I don't know how to implement them.

     We currently have 2 laptops  running 7, and two desktops running XP, one desktop in the process of troubleshooting and installing Ubuntu, one desktop with Ubuntu, and one MacBook. What I would like to do is keep the two laptops with 7, and the MacBook, but convert all the others to Ubuntu. I would like to have a home server, but not just file sharing. The only way I can explain whatever type of server it is, is by explaining it this way. Just like at most schools, I'd like the desktops to be only a login screen, and for each member of the household to have their own login username and password. When they login through either of the computers they connect to their own personalized desktop with access to their folders etc. Then if they log off someone else can log on and have access to their own. I know this is possible on individual computers with usernames and passwords, but I want it to be available across the network. So from any computer they can login and access their things. This entire connection though has to be accessible through the windows 7 computers and the MacBook. I realize that I can't use the 7 laptops and MacBook as clients like the other desktops, but as long as they can access their files I'm good. All of the files are located at the central location (the server) and can be backed up.
 
     I realize this is probably a daunting task to explain in full, but however long it takes, or if there are various threads that can assist I would appreciate any help. I am a computer science student, but only in freshman year. I am most certainly willing to learn how to master the command line and get the full functionality of Ubuntu.

     Also, just a side note. I was always curious of what happens when a program in Ubuntu or command line is running, and it gets cut short. Are there then corrupted files/"things unfinished?" I do not like incomplete things on my computer. I suppose the Windows equivalent is unnecessary registry entries or corrupt files. I am just curious to know what happens to the computer when things don't work the right way the first time, or are incomplete.

Thanks for any help.

---

### Post by SavageWolf on 2011-04-26
I think you can create /home on a central server, and have all the other ones mount it over a network, but I'm not sure how to do it.

What do you mean "cut short"? If the power is cut then there is likely to be corrupted files and such, but if you are using a SSH tunnel or control+c it should close and save the files nicely.

---

### Post by NickellossAych on 2011-04-26
By "cut short," I do mean a power outage. Or even if a command doesn't carry out the way it's supposed to. If because of some settings or software/hardware incompatibility error/issues, the command doesn't carry out properly, what happens to all of the items that were changed from the program before the error arose?

---

### Post by AllGamer on 2011-04-26
**@NickellossAych**

you basically want to setup a proper real server/client scenario corporate style (which is what school uses)

all you need to do is dedicate one of the machines as a Server, it doesn't need to have Ubuntu Server install, you can still install Ubuntu Desktop to it, but you do need to configure all the Servers components on it to work the way you want to.

Google up Ubuntu + OpenLDAP + Bind9 + Samba

example [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

you'll find many step by step Guides and HOWTOs

once you have that setup, the rest is a piece of cake, as the laptops/desktops will just login to your newly created server.

---

### Post by NickellossAych on 2011-05-06
Well, I am finding it too difficult to set up an LDAP server. I tried following a couple tutorials, but there always ends up being one thing that doesn't match up with the guide. So here's what I did. I have three Ubuntu computers, all with the newest version of Ubuntu Desktop (11.04). All of them have 5 user accounts. Across the 3 computers the same name and password is used for the individual users. So it's:

Computer 1
100g HD
user 1 password 1
user 2 password 2
user 3 password 3
user 4 password 3
user 5 password 3

Computer 2
40g HD
user 1 password 1
user 2 password 2
user 3 password 3
user 4 password 4
user 5 password 5

Computer 3
320g HD
user 1 password 1
user 2 password 2
user 3 password 3
user 4 password 4
user 5 password 5


Now, since I'm finding LDAP too difficult to do, and probably to sophisticated for home use...how can I make it so the users on computer 1 and 2 can connect to their home folders on computer 3 (since it has the biggest hard drive). Then, in theory, it's basically from whatever computer you log on to you have your same files?

OR

Is there a simpler type of "server" which requires authentication from the log on screen to connect?

---

### Post by KeyserSoze93 on 2011-05-06
I know SMB and LDAP are the new, "right" way to do it, however I've implemented just this system in the past quite happily with NIS and NFS.

Create user accounts on the server with home folders etc. This will be the PC where the files all live so it should have a large HDD.

On the designated server, install the package "nfs-kernel-server", you can then set up file shares in the /etc/exports file (see "man exports".) Set up the /home hierarchy as a shared folder with a line such as this:

```

/home           *(rw,root_squash,async,no_subtree_check,crossmnt)

```

Then install the "nis" package on the server. Give it a memorable domain name where prompted. Put the following in /etc/yp.conf:

```
#
# yp.conf       Configuration file for the ypbind process. You can define
#               NIS servers manually here if they can't be found by
#               broadcasting on the local net (which is the default).
#
#               See the manual page of ypbind for the syntax of this file.
#
# ypserver ypserver.network.com
ypserver 127.0.0.1


```

Put the following in /etc/default/nis

```

#
# /etc/defaults/nis     Configuration settings for the NIS daemons.
#

# Are we a NIS server and if so what kind (values: false, slave, master)?
NISSERVER=master

# Are we a NIS client?
NISCLIENT=false

# Location of the master NIS password file (for yppasswdd).
# If you change this make sure it matches with /var/yp/Makefile.
YPPWDDIR=/etc

# Do we allow the user to use ypchsh and/or ypchfn ? The YPCHANGEOK
# fields are passed with -e to yppasswdd, see it's manpage.
# Possible values: "chsh", "chfn", "chsh,chfn"
YPCHANGEOK=chsh

# NIS master server.  If this is configured on a slave server then ypinit
# will be run each time NIS is started.
NISMASTER=

# Additional options to be given to ypserv when it is started.
YPSERVARGS=

# Additional options to be given to ypbind when it is started.  
YPBINDARGS=

# Additional options to be given to yppasswdd when it is started.  Note
# that if -p is set then the YPPWDDIR above should be empty.
YPPASSWDDARGS=

# Additional options to be given to ypxfrd when it is started. 
YPXFRDARGS=

```

After any alterations to user accounts, as well as after the first install of nis, you must run this on the server as root:

"/usr/lib/yp/ypinit -m"

Install the "nis" package on the client machines too, as well as "nfs-common". You will be prompted to type the domain name, which should match that of the server.

On the client machines, put the following into "/etc/nsswitch.conf"

```

passwd: compat nis
group: compat nis
shadow: compat nis
hosts: files nis mdns4_minimal [NOTFOUND=return] dns mdns4
networks: files nis
protocols: db files
services: db files
others: db files
rpc: db files
netgroup: nis

```

Finally, add the following line into "/etc/fstab" on your clients:

```

192.168.1.2:/home /home nfs rsize=8192,wsize=8192,intr,timeo=14 0 0

```

(where 192.168.1.2 is the static IP of the server)

After that you should be able to log into the client machines using the user accounts from the server and get home folders and files remote-mounted.

I may have missed something but there are several guides to doing this elsewhere if you run into problems.

If you want to access users' files from non-Linux clients, see guides to setting up samba for home directories.

---

### Post by NickellossAych on 2011-05-06
I don't understand the first code you posted.

> **KeyserSoze93 said:**
> 
```

/home           *(rw,root_squash,async,no_subtree_check,crossmnt)

```

When I try that I get

bash: /home: Is a directory


I did install the nfs-kernel-server no problem.

---

### Post by IanW on 2011-05-06
> **NickellossAych said:**
> I don't understand the first code you posted.



When I try that I get

bash: /home: Is a directory


I did install the nfs-kernel-server no problem.

Do this first:-
```
gksu gedit /etc/exports
```
_Then_ paste or type in the line "/home           *(rw,root_squash,async,no_subtree_check,crossmnt)" into the file gedit opened.

---

### Post by NickellossAych on 2011-05-06
Gahhhhh okay I did that, the windows pops up where I enter the text, and I save. Then my terminal spits out 


(gedit:5829): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by NickellossAych on 2011-05-06
Okay so I'm following the guide here

[https://help.ubuntu.com/community/SettingUpNFSHowTo#NFSServer](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFSServer)

but I'm having trouble following the steps because I don't understand what exactly to do when it says 
> Edit /etc/exports and add the shares:

```
/home @myclients(rw,sync,no_subtree_check)
/usr/local @myclients(rw,sync,no_subtree_check)
```
The above shares /home and /usr/local to all clients in the myclients netgroup.

Where exactly in the file do I put those items? The beginning, the end? And every time it says to edit files I have the same problem I mentioned in the post above.

---

