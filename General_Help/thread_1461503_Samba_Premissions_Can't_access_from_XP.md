---
title: "Samba Premissions: Can't access from XP"
date: 2010-04-24
forum: General Help
---

### Post by Steve00 on 2010-04-24
I am running Ubuntu 8.10 on a HP TC1100 tablet. I installed Samba per:

<http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/>

I went into terminal and nautilus via gksudo and set my folder "Volume" to shared and set permissions.  I also edited smb.conf and set usershare owner only to false as well as added a smb user with smbpasswd. When I look at the folder in nautilus, it shows as shared.

When I go to my XP box and click on 'network neighborhoods' I can see the folder. However, when I click on it I get an error dialog that says, "\\LAPTOP||volumes is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to findn out if you havae access permissions. The network path was not found."

Windows did not ask me to login into my Ubuntu box.

My immediate need is to be able to share folders so I can transfer some large files from my Ubuntu box to my XP box.

Any suggestions?

Thank!

--Steve

---

### Post by Morbius1 on 2010-04-24
To many unknowns. Please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type [B]testparm -s

[/B]Also need to know the permissions set on your shared folder:[B]

ls -dl /path-to-shared-folder
[/B]For example, if **"**Volume" is another partition then it would be:[B]
ls -dl /media/Volume


[/B]

---

### Post by Steve00 on 2010-04-24
Thanks! Here is the info:

jk@jk-laptop:~$ net usershare info
jk@jk-laptop:~$ sudo net usershare info
[sudo] password for jk: 
[volumes]
path=/home/jk/Documents/Volumes
comment=
usershare_acl=Everyone:R,
guest_ok=y

jk@jk-laptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_DOMAIN_PDC
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	domain logons = Yes
	dns proxy = No
	usershare allow guests = Yes
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
jk@jk-laptop:~$ ls -dl /home/jk/Documents/Volumes
drwxrwxrwx 2 jk jk 4096 2010-04-22 20:59 /home/jk/Documents/Volumes
jk@jk-laptop:~$

---

### Post by Morbius1 on 2010-04-24
Other than the following line in smb.conf:
>      domain logons = YesI don't see one thing wrong with what you've posted. You might want to get rid of that unless I'm missing something else in smb.conf. After you're done restart samba:

**sudo service samba restart**

You also had no need to add an smb user because your share allows for guest access:
> [volumes]
path=/home/jk/Documents/Volumes
comment=
usershare_acl=Everyone:R,
[COLOR=Blue]guest_ok=y[/COLOR]Anyway all of this should work. 

Let's see if we can get some error messages out of WinXP:

Open **Command Prompt**
Type **net view**
Type [B]net view \\Ubuntu_Machine_Name

[/B]Not sure what the machine name is on your Ubuntu machine:
net view \\laptop
or
net view \\jk-laptop

---

### Post by Steve00 on 2010-04-24
From XP, net view results in:

Server name           Remark
----------------------------------------------------------

\\jk-laptop          jk-laptop server (Samba, Ubuntu)
\\pcwin

net view \\jk-laptop results in

Shared resources at \\jk-laptop

jk-laptop server (Samba, Ubuntu)

Share name           Type  Used as  Commment
----------------------------------------------------------
Deskjet-d410-series  Print          HP Deskjet D4100 series
volumes              Disk

---

### Post by Steve00 on 2010-04-24
BTW, the Ubuntu laptop connects to the Win XP box via wireless. I don't know if that makes a difference or not.

Thanks for the help!

--Steve

---

### Post by Steve00 on 2010-04-24
o.k., it feels like i'm soooo close....

...I disabled my firewall on my XP machine. When I did that, I was able to get further from my Ubuntu laptop than I had before.

When I went into Nautilus, I clicked on:
 Network | Windows Network | WORKGROUP | PCWIN | 

Nautilus now asks me for my user and password. Entering the password that I set with Samba does not work. I used the samba smbpasswd command to reset it to be sure.

I still can't access the Ubuntu machine from XP. Same error message as before.

---

### Post by Morbius1 on 2010-04-25
> Nautilus now asks me for my user and password. Entering the password that I set with Samba does not work. I used the samba smbpasswd command to reset it to be sure.Nautilus is not asking you for your linux password or the smb password. Nautilus is forwarding the request from Windows. Windows is requesting a user name and password before granting access to whatever shares you have on windows. Do you have any shares on Windows?

---

### Post by ds5v50 on 2010-04-25
Now that you have disabled XP's firewall, does the Ubuntu machine ask for a username password under XP's My NetWork Places? If XP's username "login" is different then the samba username it has to ask for user and password. I use the same login all across my network. My only difference is the passwords between XP and samba are different

---

### Post by Steve00 on 2010-04-25
I do have a shared folder on the XP machine (and the Ubuntu machine).

When I try to log in from the Ubuntu machine to XP, a dialog pops up on the ubuntu machine and populates the user portion with my ubuntu username.

When I try to go from XP to Ubuntu, I get the same permissions error as before.

I don't have any passwords on my XP machine. How do I set up the correct user and password in XP so that it is seen and accepted by Ubuntu?

---

### Post by Morbius1 on 2010-04-25
Why not keep things "simple" and use the same type of sharing on Windows that you have on linux - one that allows guest access .

In Windows is called "Simple Sharing"


[LIST=1]
[*]Double-click **My Computer** on the desktop.
[*]On the **Tools** menu, click **Folder Options**.
[*]Click the **View** tab, and then select the **Use Simple File Sharing (Recommended)** check box to turn on Simple File Sharing.
[/LIST]
And on the Ubuntu end, did you remove the " 			 				     domain logons = Yes" line from smb.conf and restart the samba service?

---

### Post by Steve00 on 2010-04-25
Got it. It turns out I was running under Administrator on the XP machine. Once I created a new user with password in the XP via Control Panel the Ubuntu box would see XP and let me log in.

Once I logged into the XP user, I could then see the files on the Ubuntu box.

Thanks for everyone's help!

--Steve

---

### Post by Steven_S on 2010-04-26
I'm not quite there yet... I log in to my xp machine as administrator all the time (I know, I know). Wouldn't entering the admin password just work then?

---

### Post by Steve00 on 2010-04-26
> **Steven_S said:**
> I'm not quite there yet... I log in to my xp machine as administrator all the time (I know, I know). Wouldn't entering the admin password just work then?

Dunno. I had the habit of doing the same thing on my XP box and I just couldn't get it to work with Samba. Once I added a new XP user and password (with admin rights) I was able to get Samba to behave on both the Ubuntu and XP machines. When I entered the new XP user and password on the Ubuntu box, I could then hit the XP machine. When I logged into the new XP user on the XP machine, I could hit the Ubuntu box.

Might well have been voodoo diagnostics, but it worked....

---

