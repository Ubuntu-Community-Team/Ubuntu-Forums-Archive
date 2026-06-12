---
title: "Access Ubuntu files from Windows"
date: 2011-04-04
forum: General Help
---

### Post by ubu@ on 2011-04-04
Hi,

I thought that the answer will exists on Google, but it isn't. I want to access to files created in Ubuntu on Windows OS. I found solution which work only for Windows XP /VISTA.

b.t.w, I can access freely to Windows' files from Ubuntu. even delete and change those files (i didn't installed anything). Do anyone has it in the opposite direction?

thanks!
ubu@

---

### Post by falko on 2011-04-04
You could try this: [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by ronnielsen1 on 2011-04-04
Here's two ways.

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

You might have to do the following:

> Windows Vista or Windows 7, will have problems running some older versions of applications, just because so much has changed under the hood from Windows XP days. Thankfully there is a compatibility mode that can be easily set per application.

To configure the compatibility mode for an application, just locate the installation directory and right click on the .exe, selecting Properties from the menu.
[http://www.howtogeek.com/howto/windows-vista/using-windows-vista-compatibility-mode/](http://www.howtogeek.com/howto/windows-vista/using-windows-vista-compatibility-mode/)

---

### Post by reptilezone2002 on 2011-04-04
u need samba

---

### Post by dazman19 on 2011-04-04
1) install
sudo apt-get install samba
2) create config file:
sudo gedit /etc/samba/smb.conf

[global]
 workgroup = WORKGROUP
server string = servername


[sharedata]
        comment = sharedfolder
        path = /home/daz/sharedata/
        writable = yes
        browseable = yes
        valid users = daz

3) create samba user link to user acct.
sudo smbpasswd -a <username>

sudo gedit /etc/samba/smbusers
<username> = “<username>”

4) restart samba
sudo /etc/init.d/samba restart

---

### Post by ubu@ on 2011-04-14
SAMBA is using **network** to access files. isn't? (it means that when UBUNTU is off, **can't **access files).

I have **one** computer with **two** operations system. When I'm using UBUNTU, I can freely access WINDOWS files. but not the opposite. 

about the other suggestions, I'm trying it now...

---

### Post by ubu@ on 2011-04-14
> **ronnielsen1 said:**
> Here's two ways.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)



"D:\ubuntu" folder is empty when trying to access      through the "DiskInternals Linux Reder 2.0"

---

### Post by yetiman64 on 2011-04-14
> **ubu@ said:**
> SAMBA is using **network** to access files. isn't? (it means that when UBUNTU is off, **can't **access files).

I have **one** computer with **two** operations system. When I'm using UBUNTU, I can freely access WINDOWS files. but not the opposite. 

about the other suggestions, I'm trying it now...

You are correct Samba is for networking not file access across partitions on the same machine.

You can try the previously linked ext2fs driver in Windows though it may not be all that good with ext4 iirc. Or you could set up a partition (formatted as NTFS) for both systems to access common data from.

You can use gparted from an Ubuntu live cd to repartition a drive. If you choose a separate data partition do full data backups before any repartitioning for safety.

> "D:\ubuntu" folder is empty when trying to access      through the "DiskInternals Linux Reder 2.0"      Are you using ext4 formatting on the Ubuntu install ?

---

### Post by reptilezone2002 on 2011-04-14
if both OS installed in the same  computer as dual boot tghat meens only one OS running at one time but u can access windows partions thrugh ubuntu bunt u cant access linux partitions from windows thats y u have to share linux partitions through the network with SAMBA  ubuntu must be running at the time to access ubuntu files from windows through samba

am i right guys!!!!!

---

### Post by yetiman64 on 2011-04-14
> **reptilezone2002 said:**
> **if both OS installed in the same  computer as dual boot tghat meens only one OS running at one time** but u can access windows partions thrugh ubuntu bunt u cant access linux partitions from windows thats **y u have to share linux partitions through the network with SAMBA**  ubuntu must be running at the time to access ubuntu files from windows through samba

am i right guys!!!!!

No.

First bolded section above is correct, think about what you have said here IF Windows is active then Ubuntu is NOT, hence Samba is of no use (Windows and Ubuntu HAVE to be on 2 separate machines to use Samba sharing and that is not the case as written here). The OP is asking about accessing files across Windows and Ubuntu partitions on the SAME machine.

---

### Post by ubu@ on 2011-04-15
> Are you using ext4 formatting on the Ubuntu install ?     I guess its ext4...

[ I used the command *mount*, and the first line *is*:[I]
 /dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
[/I] ]

---

### Post by yetiman64 on 2011-04-15
> **ubu@ said:**
> I guess its ext4...

[ I used the command *mount*, and the first line *is*:[I]
 /dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
[/I] ]

Yes, you're on ext4 then. Some windows utilities don't work so well with it. Haven't myself heard of any good ones for the job yet.

---

### Post by ubu@ on 2011-04-15
> **yetiman64 said:**
> ...Or you could set up a partition (formatted as NTFS) for both systems to access common data from.


I think I will settle on this solution.

But should I set this thread as SOLVED? or wait for someone to come up with solution requires only installing some software?

thanks for all,
ubu@

---

### Post by reptilezone2002 on 2011-04-16
> **ubu@ said:**
> I think I will settle on this solution.

But should I set this thread as SOLVED? or wait for someone to come up with solution requires only installing some software?

thanks for all,
ubu@



i think its solved thats how im using if u want to share files between windows & linux use a separate partition for that (NTFS) its simple & it works :guitar:

---

