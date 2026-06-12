---
title: "Samba share attributes"
date: 2010-04-10
forum: General Help
---

### Post by derek71 on 2010-04-10
I have Samba 3 installed under Ubuntu server 8.04 LTS.  I have basic sharing working with my Windows XP machine though I want to make the share behavior transparent to the Windows user.  I have created my share directories on a ext3 file system.

I want to preserve the windows file attributes and create/modified dates for the files stored on the share.  I use a commercial nas at work, and I noticed that the file attributes and timestamp information is preserved.  I wondered if this were possible with Samba/CIFS?

For preserving the file attributes, I have researched the question and have found references to Samba commands as: map archive = , map hidden, and map system.. etc.  I have tried these options without success.

Researching the timestamp options, I have found references to enabling extended attributes for a file system, though I don't know how this is implemented or for what file systems.

---

### Post by drdos2006 on 2010-04-11
If you want Windows to be able to read and write to your shared folders, then you need a folder that Windows can read. Windows can read NTFS but not ext3.
regards

---

### Post by derek71 on 2010-04-11
With ext3 I can read/write to the Samba server.  I am looking to preserve the file attributes: permissions, create/modify dates.

Would an NTFS system provide this capability?

In my readings, there is an extended file attributes flag that can be added to the fstab entry for the mount point of the share.

---

### Post by capscrew on 2010-04-11
> **derek71 said:**
> With ext3 I can read/write to the Samba server.  I am looking to preserve the file attributes: permissions, create/modify dates.

Would an NTFS system provide this capability?

In my readings, there is an extended file attributes flag that can be added to the fstab entry for the mount point of the share.

XP does not care what filesystem is on Ubuntu.  The data is displayed via SMB (which is native to Windows).  The problem is translating the timestamp only.

I would use classic shares rather than usershares (created via Nautilus (GUI).  You can then configure the share via /etc/samba/smb.conf.

See [**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")for all smb.conf parameters.

---

### Post by derek71 on 2010-04-11
Is there a command line interface to create these shares?  I have the server version of Ubuntu installed.

What is a classic share versus the shares I have created in the smb.conf file?

---

### Post by capscrew on 2010-04-11
> **derek71 said:**
> Is there a command line interface to create these shares?  I have the server version of Ubuntu installed.

What is a classic share versus the shares I have created in the smb.conf file?

A classic share is created at the CLI via configuring the /etc/samba/smb.conf file.  I use VIM to edit the smb.conf file.  You must be doing it in the classic manner.

You mentioned permissions -- I use the *force *parameter for groups and *unix extensions*.  The defaults for this have chaged in the last month, so the documentation may be different from the latest defaults.  

The way I have done it was geared towards Linux (posix) rather than Windows (NTFS), but I have seen that the file ownership as viewed using either XP or Vista is correct.  I have no problems using EXT3 on the Ubuntu server.

The usershares that I referred to are generally created via the GUI interface (Gnome Nautilus or the like in KDE).  it sounds like usershares are irrelevant to your installation. 

I would Google timestamps for NTFS and EXT3 (or Ext4).  There is a good amount of information.

---

### Post by derek71 on 2010-04-15
I have done some digging on storing the windows file timestamps on Samba and looks like enabling the extended attributes option for the file system and within Samba would preserve the file attributes though not sure about the dates.

Would Active Directory allow this information to be preserved?

---

### Post by capscrew on 2010-04-15
> **derek71 said:**
> I have done some digging on storing the windows file timestamps on Samba and looks like enabling the extended attributes option for the file system and within Samba would preserve the file attributes though not sure about the dates.

Would Active Directory allow this information to be preserved?

Active Directory has nothing to do with timestamps on file systems.  AD is for authenticating users (KERBROS) and managing them (LDAP and GPO).  It also has network management functions(DNS). 

The date problem is due to the differing methods of calculating time by MS and Linux.

---

### Post by derek71 on 2010-04-15
I know linux/unix does not store separate create/modify time stamps natively.  Would a different file system address this problem for Samba?

---

### Post by capscrew on 2010-04-15
> **derek71 said:**
> I know linux/unix does not store separate create/modify time stamps natively.  Would a different file system address this problem for Samba?

Linux/unix itself does not store the timestamps.  You are correct in that the file system itsef does.  See [**_here _**]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")for comparisons of file systems.  Check the *Metadata * grid for what you are looking for.

There are 2 things to note.  Both Ext4 and BtrFS use creation time stamps. Both come with their own baggage so to speak.  There have been cases of Ext4 losing data (this is for specific reasons, but the argument remains).  The BtrFS is really the way to go in the future, but it is at the beta stage right now.

---

### Post by derek71 on 2010-04-16
Capscrew,

Thank you for the very informative link.... 

Comparing to NTFS, there looks to be several file systems that would work: ZFS is current and supported under linux and the notes indicate that the DOS file attributes are stored.

Since Windows XP is NTFS native (true NTFS?), would this be the safest bet for storing files and preserving attributes via linux ntfs-3g?

Through Samba or even a network protocol like SSH, would the file system appear as NTFS with all of its attributes, or only the portions of it used by Ubuntu?

---

### Post by capscrew on 2010-04-16
> **derek71 said:**
> Capscrew,

Thank you for the very informative link.... 

Comparing to NTFS, there looks to be several file systems that would work: ZFS is current and supported under linux and the notes indicate that the DOS file attributes are stored.

Since Windows XP is NTFS native (true NTFS?), would this be the safest bet for storing files and preserving attributes via linux ntfs-3g?

I would say NTFS is what you should try.  The ZFS file system is a totally different system with complications.  See [**_here _**]("http://en.wikipedia.org/wiki/ZFS")for information.  Nextenta is a Debian distro that is using ZFS as the file system.  See [**_here_**]("http://www.nexenta.com/corp/").

The BtrFS file system will be a Linux based file system that has ZFS features.  This is what I am waiting for.
> 

Through Samba or even a network protocol like SSH, would the file system appear as NTFS with all of its attributes, or only the portions of it used by Ubuntu?

I'm not sure.  When it is all said and done, trying it is the only way to know.

---

