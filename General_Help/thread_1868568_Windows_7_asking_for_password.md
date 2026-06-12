---
title: "Windows 7 asking for password"
date: 2011-10-24
forum: General Help
---

### Post by Stevek33 on 2011-10-24
I am a complete noob. I have been making slow progress.
 
I now can see my ubuntu shared folders on the network BUT...
 
When I click on the shared folders windows pops a screen asking for "Enter Network Password"
 
User Name
Password
 
I have checked the smb.conf and cannot see anything that I can change.
 
So how can I completely disable the password for my windows 7 machines?

---

### Post by TeoBigusGeekus on 2011-10-24
A quick googling gave me [this]("http://www.linuxquestions.org/questions/linux-newbie-8/samba-ask-password-at-windows-explorer-821426/").

---

### Post by Stevek33 on 2011-10-24
> **TeoBigusGeekus said:**
> A quick googling gave me [this]("http://www.linuxquestions.org/questions/linux-newbie-8/samba-ask-password-at-windows-explorer-821426/").
 
Teo thanks for the info.  I tried following the instructions and it still needs a password from my windows machines.  UGH!

---

### Post by Stevek33 on 2011-10-24
*bump*
 
Does anyone know how to disable passwords?  From my windows 7 machines when I click on the folders that are shared from Ubuntu it opens a password box.  ???

---

### Post by LinuxFan999 on 2011-10-24
I had this exact same problem once when trying to connect an Ubuntu Virtualbox guest to the Host, which runs Windows Vista SP1. The Host has no password, but the guest will ask me for one, and no matter what I type in, Ubuntu won't accept it.

---

### Post by Stevek33 on 2011-10-24
I am new to Ubuntu. I have it all installed and configured. I configured samba. I shared the folders I wanted.
 
On all my windows7 machines (3) I can see the server and files but when I try to open the folders a User Name and Password window pops up.
 
I would like free access to all my windows machines. How can I get the password protection disabled?
 
Thanks in advance!:D

---

### Post by Stevek33 on 2011-10-24
:(
 
Anyone?  Still patiently waiting for some help.

---

### Post by Stevek33 on 2011-10-24
No one has had this problem?  I have looked everywhere and cannot find anything.  Please help!

---

### Post by Diametric on 2011-10-24
Might want to check on a windows forum for that info.  I'm sure a search could get you the info you need.

---

### Post by dFlyer on 2011-10-24
I can't answer your question, I haven't used windows in many years so know nothing about win7. I justed in because don't need to start a new thread. you already have one opened just 9 hours ago. Be patience and someone will have an answer for you. 9 hours is not a long time to wait on such matters.

[http://ubuntuforums.org/showthread.php?p=11390016#post11390016](http://ubuntuforums.org/showthread.php?p=11390016#post11390016)

---

### Post by papibe on 2011-10-24
Could you post the result of this command?
```
$ sudo testparm
```
Please paste your results using the # tags.
Regards.

---

### Post by Elfy on 2011-10-25
Please do not post duplicates, it dilutes community effort. Threads merged.

---

### Post by Stevek33 on 2011-10-25
> **papibe said:**
> Could you post the result of this command?
```
$ sudo testparm
```
Please paste your results using the # tags.
Regards.
 
Thanks Papibe!
 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Myshare]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANALONE
Press enter to see a dump of your service definitions

---

### Post by papibe on 2011-10-25
> **Stevek33 said:**
> 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[Myshare]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANALONE
**Press enter to see a dump of your service definitions**
Hey Stevek33, you missed one step. If you read the last line, you have to press enter in order to display the relevant information.

Regards.

---

### Post by Stevek33 on 2011-10-25
> **papibe said:**
> Hey Stevek33, you missed one step. If you read the last line, you have to press enter in order to display the relevant information.

Regards.

Yeah i wasn't sure if you needed that or not.  So here it is.  Thanks again!

[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[Myshare]
    comment = Myshare
    path = /Myshare
    read only = No
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by papibe on 2011-10-28
Is your Windows' user the same (or very similar) to your user in the Ubuntu machine?

Regards.

---

### Post by critin on 2011-10-28
I'm checking my setup but I use XP so it may be easier than 7.  I don't use passwords to reach xp from ubuntu, but I've never tried from xp to ubuntu because I work on ubuntu all the time.   Give me a few min.
Thanks.

---

### Post by dariusdwtt on 2011-10-28
Your best bet is to set a password on the XP machine, and then set the sharing perms correctly.
Also disable that recommended sharing thing, at the bottom of the list in the windows folder options thing. I think it's the sharing wizard, or simple file sharing, disable it?

PS, I think your problem is windows related. I think most people here won't really be that interested, after all, these are the Ubuntu Forums?

---

### Post by critin on 2011-10-28
I think it's a windows problem.  Ubuntu sets up the network when installing so I can immediately use it out.  Windows requires a network be set up, and shows the workgroup but won't let me in.  

I suggest visiting the Windows forum for this issue.

Can you get to windows from ubuntu?   Can you open and edit files from ubuntu?

---

### Post by Stevek33 on 2011-10-29
> **critin said:**
> I think it's a windows problem. Ubuntu sets up the network when installing so I can immediately use it out. Windows requires a network be set up, and shows the workgroup but won't let me in. 
 
I suggest visiting the Windows forum for this issue.
 
**Can you get to windows from ubuntu? Can you open and edit files from ubuntu**?
 
I haven't thought about looking at it the other way. I tried and couldn't figure out how to point at my W7 machine.  UGH!  This is getting beyond frustrating.  About to just bag it.  :confused:

---

### Post by critin on 2011-11-04
Did you get it working?
Network in 'Places' is always setup automatically for me in ubuntu, and it always sees and opens the microsoft lan perfectly.  I can view, change, or whatever to the window machines from ubuntu.  

From xp though, after setting up network,  it shows the ubuntu machine in the Workgroup, but it won't let me open it.  It did once on some version of ubuntu, but I've changed the OS since then and have no idea what the difference was or what I did to make it work.  It's number six in my list of things to find out and learn.  Not high priority as long as ubuntu can do the job.  Windows forums were no help for me.  Guess they don't do linux.   :P

---

### Post by Flaggmann on 2011-11-04
If it is a standard windoze peer-peer arrangement, the same userid has to be on both pc's to get access to the shares. the win uid has to be the one that created the share or at least have permissions assigned.  If ur linux user id is the same and uses the same password, I found that works OK. Otherwise you might have ti get complicated and less secure and use a generic guest user etc which gives the guest user permissions on the shred folders as well.

I found the easiest answer was to set up NFS and then dual boot the win pc with a distro of linux that auto defaults mounting the the win drives then copy the files you want to share into the NFS shares and go from there. Keeps net simple and better security then user a USB stick or dropbox to do minor updates.




> **Stevek33 said:**
> :(
 
Anyone?  Still patiently waiting for some help.

---

### Post by critin on 2011-11-11
> I found the easiest answer was to set up NFS and then dual boot the win pc with a distro of linux  that auto defaults mounting the the win drives then copy the files you  want to share into the NFS shares and go from there. Keeps net simple  and better security then user a USB stick or dropbox to do minor  updates.

Thanks Flaggmann!  I'm going to do this on one Windows mach. and see how it works from the others.   I hadn't thought of it.  :P   I've read ubuntu from Windows in a past connection but can't do it now.

---

