---
title: "How does SAMBA map user permissions?"
date: 2012-03-29
forum: General Help
---

### Post by Budric on 2012-03-29
Hi,
I'm configuring samba shares and trying to understand permissions.  File system permissions trump any samba write/read lists.  How does samba map authenticated users via smbpasswd to linux users?

If there's ubuntu user bob, and authenticated samba user bob.  Does smbd try to match the two bob users and access file using that user account?

If there's no linux user bob, but a samba user bob and smb.conf doesn't specify that system user must exist.  What file permissions apply then?

When does sambashare group get used?

How does Ubuntu right click and "Share Folder" work?  None of those shares are in smb.conf file.  Is it done through samba?  Can I setup my samba to use only linux accounts and skip smbpasswd altogether?

Thanks.

---

### Post by bab1 on 2012-03-29
> **Budric said:**
> Hi,
I'm configuring samba shares and trying to understand permissions.  File system permissions trump any samba write/read lists.  How does samba map authenticated users via smbpasswd to linux users?

As far as I know you have to have ***both*** a OS user (Ubuntu) and a Samba user (via smbpasswd) for Samba to work.  The only exception is the guest account.  See below.> 

If there's ubuntu user bob, and authenticated samba user bob.  Does smbd try to match the two bob users and access file using that user account?
Yes, to Samba they are the same user.> 

If there's no Linux user bob, but a samba user bob and smb.conf doesn't specify that system user must exist.  What file permissions apply then?
If user is not found in unix passwd" and you have "*map to guest = bad user" * Samba maps to the system user **nobody** by default. > 

When does sambashare group get used?
That's a Linux group and you get to define when it's used.  The package routines make the group not Samba.> 

How does Ubuntu right click and "Share Folder" work?  None of those shares are in smb.conf file.  Is it done through samba? 
These are called *usershares*.  These shares are located in /var/lib/samba/usrshares.  Samba creates the shares via Nautilus, but you can also create them from the terminal.>  

Can I setup my samba to use only linux accounts and skip smbpasswd altogether?

Nope, you have to have both or the user is a guest if you set guest access up.

---

### Post by SeijiSensei on 2012-03-29
Samba does offer an often useful alternative, the "force user" and "force group" directives.  With these you can define a share that is owned by a single Unix user and group for OS-level activities regardless of the identity of the users logged into the share.  That does mean all the files will be owned by the common user, so that you can't discriminate between files created by bob and ones created by ted.  If you don't care about that, then the "force" directives might be useful.

In this case, I believe that you don't need a corresponding Unix user/group for each Samba user/group.

Type "man smb.conf" at a Terminal prompt for more details.

---

### Post by bab1 on 2012-03-29
> **SeijiSensei said:**
> Samba does offer an often useful alternative, the "force user" and "force group" directives.  With these you can define a share that is owned by a single Unix user and group for OS-level activities regardless of the identity of the users logged into the share.  That does mean all the files will be owned by the common user, so that you can't discriminate between files created by bob and ones created by ted.  If you don't care about that, then the "force" directives might be useful.

In this case, I believe that you don't need a corresponding Unix user/group for each Samba user/group.

Type "man smb.conf" at a Terminal prompt for more details.
The force user and force group work like *suid* and *sgid*.  They do nothing to help in authenticating the user.  I believe you have to *at least* be authenticated as "guest" to access the share data.

The information regarding user/group security is in the smb.conf man pages in the section under **Security (G)**.  The default is *security = user*.  From the description: "Note that smbd **ALWAYS** uses a ***valid UNIX user*** to act on behalf of the client, even in security = share level security."

---

### Post by Budric on 2012-03-30
Thanks guys.

---

### Post by Morbius1 on 2012-03-30
There is one peculiarity about how clients browse and attempt to access  shares that might just save you from going insane when it come to all  this and it depends on what OS the client is using.

_**Windows Client**_
Let's say you have a Windows user named morbius and he logs  into his Windows box with that user name and a password of xyz. When  morbius tries to access a share, Windows passes that username and  password automatically. Assuming you have the parameter "map to guest =  Bad User" and you have created a share requiring credentials what  happens is this:

* If you have created a user on Linux named  morbius and have set the samba password to xyz the Windows user is allowed in to the share automatically  without being prompted.

* If you have a username that matches but a samba password that does not, the Windows user will be prompted for credentials.

* If you have no Linux user  named morbius and therefore no samba password for him then the Windows  user will be converted to "nobody" because of "map to guest = Bad User"  and "guest account = nobody ( which is in the defaults but is not in  smb.conf" ) and "nobody" is denied access.

_**Linux OS**_
The Linux client works differently in that it does  not automatically pass the users login name and password ( at least not  if it browses to and selects a share ) since Samba thinks that's goofy.  Linux clients will always be asked for credentials and "map to guest"  really plays no role.

_**Guest share**_
The reason I bring this up is because  you may decide to create a "guest share" where you are allowing anyone  to access the share. The Windows user who has a corresponding Linux user  / samba password match will be allowed access and will save a file with  that user name.

If the username matches but the password does  not the Windows users will be prompted for credentials to access the  quest share because the Linux server is forced to resolve the  credentials that have already been passed. [COLOR=Blue]This is done at the Hostname  level even before it reaches the share.[/COLOR]

If there is no Linux user / smb password then the user comes across as "nobody"and access is granted and files will be save with owner = nobody. The Linux  client will always come across as "nobody" so if you have a mix of client  OS's you could have a mixture of files saved as "nobody", "morbius",  .....

As pointed out above "force user" and "force group" can be  used to equalize things on the server. These parameters take affect after the  authentication phase of samba and it will make all files saved have the same owner, group, or both.

---

