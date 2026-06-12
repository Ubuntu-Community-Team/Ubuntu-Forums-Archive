---
title: "Give a User FULL Permissions - Via SSH"
date: 2012-04-30
forum: General Help
---

### Post by mrchasez on 2012-04-30
I need too give user "user1" permission to read/Write in any directory, in any file.

I have sudo perms.
Please don't make this complicated, i am a novice.
One line commands preferred.

I do not want every group to have these permissions
Just the user "user1"

Thanks

---

### Post by Zill on 2012-04-30
mrchasez:  This document may help explain things...

[Editing Files that Belong to Root]("http://www.psychocats.net/ubuntu/permissions")

---

### Post by JRV on 2012-04-30
Welome aboard!

Click the purple icon in the upper right corner.
Click System Settings.
Double click User Accounts.
Click Unlock and enter your password.
Select the user1 account.
Change Standard to Administrator.

---

### Post by mrchasez on 2012-04-30
> **JRV said:**
> Welome aboard!

Click the purple icon in the upper right corner.
Click System Settings.
Double click User Accounts.
Click Unlock and enter your password.
Select the user1 account.
Change Standard to Administrator.

I only have SSH.

---

### Post by mrchasez on 2012-04-30
> **Zill said:**
> mrchasez:  This document may help explain things...

[Editing Files that Belong to Root]("http://www.psychocats.net/ubuntu/permissions")

Can you just give me the answer?

---

### Post by philinux on 2012-04-30
> **mrchasez said:**
> I only have SSH.

I've amended the title of the thread to reflect the use of SSH.

---

### Post by Cheesemill on 2012-04-30
```
sudo adduser user1 sudo
```Will add user1 to the sudo group, they will then be able to use sudo to make any changes they wish.

---

### Post by Zill on 2012-04-30
> **mrchasez said:**
> Can you just give me the answer?
If you are "user1" *and* you have "sudo perms" then you already have full permissions to "read/Write in any directory, in any file".

Please read the link I posted earlier explaining how to use sudo.

---

### Post by mrchasez on 2012-04-30
> **Zill said:**
> If you are "user1" *and* you have "sudo perms" then you already have full permissions to "read/Write in any directory, in any file".

Please read the link I posted earlier explaining how to use sudo.

I can use Sudo just fine.
I try to open a file in /home/minecraft/multicraft
I get this error

Received error message from remote side: 'scp: /home/minecraft/multicraft/multicraft.conf: Permission denied'

However, I can use sudo.

---

### Post by mrchasez on 2012-04-30
> **Cheesemill said:**
> ```
sudo adduser user1 sudo
```Will add user1 to the sudo group, they will then be able to use sudo to make any changes they wish.

user1@(stuff):~$ groups
user1 adm cdrom sudo dip plugdev lpadmin sambashare

No admin group

---

### Post by Cheesemill on 2012-04-30
> **mrchasez said:**
> user1@(stuff):~$ groups
user1 adm cdrom sudo dip plugdev lpadmin sambashare

No admin group
Yep, my mistake. I edited my post with the correct command.

---

### Post by Zill on 2012-04-30
> **mrchasez said:**
> ...Received error message from remote side: 'scp: /home/minecraft/multicraft/multicraft.conf: Permission denied'...
Please post the exact terminal command(s) you used.

---

### Post by mrchasez on 2012-04-30
> **Zill said:**
> Please post the exact terminal command(s) you used.

That wasn't using the terminal.
I was trying to open the file using WinSCP

---

### Post by mrchasez on 2012-04-30
> **Cheesemill said:**
> ```
sudo adduser user1 sudo
```Will add user1 to the sudo group, they will then be able to use sudo to make any changes they wish.

The user `user1' is already a member of `sudo'.

See, I can use any Sudo commands.
but when trying to delete / Open some files using WinSCP.
I dont have permission.

---

### Post by mrchasez on 2012-04-30
Help ;P

---

### Post by nothingspecial on 2012-04-30
Please do not bump your thread so quickly. About once every 24 hours or so is best.

---

### Post by mrchasez on 2012-04-30
> **nothingspecial said:**
> Please do not bump your thread so quickly. About once every 24 hours or so is best.

Thought it was a simple question ;/

---

### Post by Zill on 2012-04-30
> **mrchasez said:**
> That wasn't using the terminal.
I was trying to open the file using WinSCP
I don't use any MS/Windows products here but would have thought that WinSCP is primarily a GUI application.  I *guess* this will make it difficult for you to ssh into a Linux system and still use a command that needs the sudo prefix, and associated password authorisation.

If you can ssh into the Linux PC via a terminal then things may be simpler. ;-)

---

### Post by CharlesA on 2012-04-30
> **Zill said:**
> I don't use any MS/Windows products here but would have thought that WinSCP is primarily a GUI application.  I *guess* this will make it difficult for you to ssh into a Linux system and still use a command that needs the sudo prefix, and associated password authorisation.

If you can ssh into the Linux PC via a terminal then things may be simpler. ;-)
Their user would need read access to copy a file via sftp or scp even when using them from a terminal.

---

### Post by Zill on 2012-04-30
> **CharlesA said:**
> Their user would need read access to copy a file via sftp or scp even when using them from a terminal.
Agreed.  I think it would be helpful if the OP clarified exactly what he/she is trying to do!  We need to know more details about how the machine(s) are configured and the permissions of the various users.

---

### Post by CharlesA on 2012-04-30
> **Zill said:**
> Agreed.  I think it would be helpful if the OP clarified exactly what he/she is trying to do!  We need to know more details about how the machine(s) are configured and the permissions of the various users.
Yep. It would be helpful to know permissions that directory has. It should have defaulted to rwxrwx-r-x

---

