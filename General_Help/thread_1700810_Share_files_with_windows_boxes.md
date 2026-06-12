---
title: "Share files with windows boxes"
date: 2011-03-05
forum: General Help
---

### Post by Beowolf64 on 2011-03-05
I am having trouble sharing files between Ubu and Win boxes.

We have seval boxes hooked up to the same router. XP and Vista boxes are part of the same workgroup (lets call it FOO). No domain. It is a simple home network. Each Win box has its own name. Win boxes can see each other (by clicking Network icon from control panel). Shared resources can be accessed by providing user name and password. Now I need to make Maverick box a part of the the same workgroup. All group members should be able to access Maverick's shared recourse by providing user name and password and vice versa. 

I installed samba (is that what I need?), but couldn't get things working yet. Official [docs]("https://help.ubuntu.com/10.10/internet/C/connecttoserver-windowsshare.html") aren't very clear. What is the server name and domain? Win boxes don't need any of that. I can just click network icon and go into any computer I want. What are the steps to setup Ubu box similarly? Any step-by-step tutorial for dummies would be very helpful!

Samba docs say edit smb.conf file. I have 2 in my box :

/usr/share/samba/smb.conf
/etc/samba/smb.conf

Which one is for editing.
Where do I put FOO (our work-group name)?
How to set permissions?
Anything else?


Thank s in advance.

---

### Post by Morbius1 on 2011-03-05
I sincerly hope this doesn't end up being more confusing but there are two ways to create a samba share.

Classic-share: The samba configuration file and share definitions are located at: /etc/samba/smb.conf.

Usershare ( a.k.a. Nautilus-share ): Part of it is controlled by smb.conf but the share definitions are at: /var/lib/samba/usershares. You really don't alter the share definitions there you create then through Nautilus.

My recommendation is to use Usershare first since it's the easiest to use and resembles a WinXP "Simple Share" ( on steroids ) in how you create a share. The following will create a guest accessible share that does not require authentication ( we can add users and passwords later when we know everything is working ):

Open Nautilus
Right click a folder you own say ... Documents
Select "Sharing Options"
At this point if you don't have Samba installed it will ask you if you want to install it - you do.
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
It will ask you if you want it to modify permissions - you do.
Done

If you want to have your box on the same workgroup you'll have to change that manually however:

Edit /etc/samba/smb.conf and change the following line to whatever you want:
> # Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = **[COLOR=Blue]workgroup[/COLOR]**
Save smb.conf and restart samba:
```
sudo service smbd restart
```Now as a test run the following command:
```
smbtree
```It will list every workgroup and within every workgroup every host and within every host every share. If it runs into difficultly it may post an error message.

If you can see your new share then try to access it from your Windows machines.

---

### Post by Primefalcon on 2011-03-05
Way I've done it

just go to software centre, install samba
go to system=>admin=>samba
go to samba users and add yourself to the list

then simply right click on any folders you want to share with windows

with windows simply right click create shortcut and enter local IP of the buntu computer as the shortcut location, from then on you can use that shortcut to browse the shared on the buntu computer from windows

---

### Post by Morbius1 on 2011-03-05
> **Primefalcon said:**
> forget the config files......

just go to software centre, install samba
go to system=>admin=>samba
go to samba users and add yourself to the list

then simply right click on any folders you want to share with windows

with windows simply right click create shortcut and enter local IP of the buntu computer as the shortcut location, from then on you can use that shortcut to browse the shared on the buntu computer from windows
This is why I try to avoid going into the forum on the weekends.

Why on earth would he want to add his own username to the smbpasswd database? Do you want the remote user to use the server users username to access the share? What about the password? Do you want the samba password to match the server users login password? Why have users or passwords at all at that point.

---

### Post by Primefalcon on 2011-03-05
> **Morbius1 said:**
> This is why I try to avoid going into the forum on the weekends.

Why on earth would he want to add his own username to the smbpasswd database? Do you want the remote user to use the server users username to access the share? What about the password? Do you want the samba password to match the server users login password? Why have users or passwords at all at that point.
I said add yourself to th list as in an account for yourself... not to enter the same password as the user system...

though to be honest on my home system I just use anonymous access anyhow since the only people access the shares are my wife and myself anyhow....

for work enviro's I use ssh/sftp solely.

---

### Post by Morbius1 on 2011-03-05
There's never any need to add the server users name to the smbpasswd database. At least not in a peer-to-peer like samba environment that one has in a home lan. It would serve no purpose.

---

### Post by Beowolf64 on 2011-03-06
Thanks everyone for the input. It turned out that **connman** broke the network manager. Related [thread]("http://ubuntuforums.org/showthread.php?t=1594566"). I will try again once I fix the Ubu boxes.

---

### Post by Beowolf64 on 2011-03-14
OK. Got it working. Partially. Win boxes can see samba shares and other Win shares, but Ubu boxes can see neither Win shares nor other samba shares. What could be wrong? Maybe I am trying to browse a wrong place? Is it ***Places->Network***?

---

### Post by blueridgedog on 2011-03-14
This sums up the process:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

One thing to check is that user accounts are the same on the systems or all files are shared wide open permission wise.  If I don't have an account on a windows machine and we are not using a domain, I won't see files on that machine.  Typically that means setting up matched sets of users on all systems that share files in a mixed network without a central authentication server of some type.  So, for example on my daughter's windows system, I have a user account that matches my account on my Linux system, I can then browse shares on her system easily.  She too has an account on my Linux system and can access her files and those open to the public (I created her account, then used the smbpasswd program to enable it for samba access).

---

### Post by Beowolf64 on 2011-03-15
Thanks everyone. Looks like it is SOLVED.

---

### Post by blueridgedog on 2011-03-15
What was the final change that enabled things to work as you wish?

---

