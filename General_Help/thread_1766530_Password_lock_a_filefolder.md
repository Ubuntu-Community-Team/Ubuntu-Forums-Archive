---
title: "Password lock a file/folder?"
date: 2011-05-24
forum: General Help
---

### Post by .psd on 2011-05-24
What's the easiest way to make a given file/folder (or multiple files) require a password upon opening moving copying etc, without encrypting the file/archive. The password should at least be manually defined upon establishing it, and preferably it could be modified.

I'm aware of the community belief that this is redundant. I don't want to know how to start from scratch a different way, or why I should or shouldn't do this or that. Just how to password lock a file/folder regardless of your feelings on the matter lol.

---

### Post by Megaptera on 2011-05-24
This answer may be bit basic perhaps, but what about a separate User Account? That way you'd have one public account for day to day stuff and your personal files under a separate user account with different p/w?

Or, from here:

[http://askubuntu.com/questions/4796/how-can-i-simply-password-protect-a-file](http://askubuntu.com/questions/4796/how-can-i-simply-password-protect-a-file) "could you use the Archive Manager to zip the file and password protect the zip file? I think to do this right click on the file and choose "Compress" then choose zip as the archive type and in "Other options" you have the option to enter a password.

This is simple to do and stops the problem of someone mounting the file system from a live CD and getting the file that way.

Also you can easily email the file or copy to USB stick, etc without having to worry about having the means to unencrypt the files at the other end, you just need the password."

---

### Post by enimeizoo on 2011-05-24
I'm not sure, but I think that if you don't encrypt a file, at least root will be able to read it without a password. You can make it unreadable by non-sudoers by playing with the permissions (actually, have root own it and set the rights to 700)

I think what you need is encrypting. It would be the easiest way of achieving what you want. It is also safer since even root can't decrypt without the key (someone booting with a livecd can have root access to your files for example).

(edit) when you password-protect a zip file, it is encrypted, isn't it?

---

### Post by .psd on 2011-05-25
Thanks for the help but like I explained in the OP, the only thing I'm trying to accomplish is to learn how to password lock a file/folder. I know about encrypting, or different users.

Preferably I'd always be superuser. Is that possible? Opinions/alternatives aside.

---

### Post by satish_j on 2011-05-25
well,i don't think this is possible to achieve w/o encryption..

---

### Post by Megaptera on 2011-05-25
> **.psd said:**
> Thanks for the help but like I explained in the OP, the only thing I'm trying to accomplish is to learn how to password lock a file/folder.


Have you looked at this option in my answer #2?

[http://askubuntu.com/questions/4796/...protect-a-file](http://askubuntu.com/questions/4796/...protect-a-file) "could you use the Archive Manager to zip the file and password protect the zip file? I think to do this right click on the file and choose "Compress" then choose zip as the archive type and in "Other options" you have the option to enter a password.

This is simple to do and stops the problem of someone mounting the file system from a live CD and getting the file that way.

Also you can easily email the file or copy to USB stick, etc without having to worry about having the means to unencrypt the files at the other end, you just need the password."

---

### Post by .psd on 2011-05-25
> **Megaptera said:**
> Have you looked at this option in my answer #2?

[http://askubuntu.com/questions/4796/...protect-a-file](http://askubuntu.com/questions/4796/...protect-a-file) "could you use the Archive Manager to zip the file and password protect the zip file? I think to do this right click on the file and choose "Compress" then choose zip as the archive type and in "Other options" you have the option to enter a password.

This is simple to do and stops the problem of someone mounting the file system from a live CD and getting the file that way.

Also you can easily email the file or copy to USB stick, etc without having to worry about having the means to unencrypt the files at the other end, you just need the password."
Ya, that would be the default workaround if linux was seriously so ridiculous as to not implement at least one method for password locking a file or folder. I'm hoping linux isn't that ridiculous so I came here to find out.

I'm not afraid of anyone hacking my files, I don't need *any* protection other than a simple password requirement. As I said, if I can enable and permanently become superuser, that is my preferred solution. I'm aware of all the dangers this implies.

---

### Post by linuxinstalledfromhdd on 2011-05-25
It's really not recommended to become superuser.  But it is possible, and yes it does open you up to all kinds of security issues potentially.  It would mean that you are logged in as root user and no password required.  Then Chmod whatever you don't want other users to access. read. execute. etc.

---

### Post by papibe on 2011-05-25
AFAIK there's no way to protect regular directories/files in your system from the super user (network shares are different).

The only way would be to use some sort of encryption. If I understand correctly you don't want decrypt your files every time you need to use them, and of course encrypt right after to protect them.

The alternative would be to use a comprehensive application that would be transparent for you. So that it will ask you for a password every time you want to see a file, or enter a directory.

If that is closer of what you're looking for, take a look at [TrueCrypt ]("https://help.ubuntu.com/community/TrueCrypt")and [encfs]("https://help.ubuntu.com/community/FolderEncryption").

---

### Post by .psd on 2011-05-25
> **linuxinstalledfromhdd said:**
> It's really not recommended to become superuser.  But it is possible, and yes it does open you up to all kinds of security issues potentially.  It would mean that you are logged in as root user and no password required.  Then Chmod whatever you don't want other users to access. read. execute. etc.
Perfect! What do I do?

Like I said, I don't need to protect anything from anyone locally. My network is one computer and a wife.

I would like everyone to have access to everything at all times, with the exception of files I decide. As it is, my wife and I can hardly do anything because of how complicated the security and learning process is. I would like to password lock some files and folders. I don't care how "safe" this is, as long as when someone double clicks on certain files to open them, a password prompt will appear.

> **papibe said:**
> AFAIK there's no way to protect regular  directories/files in your system from the super user
That's fine. My wife and I *are* the superuser. We have both grown up perfectly fine on ultra-unsafe Windows.

---

### Post by skyiscrying on 2011-07-19
I think you may was well dump your secret files on a USB flash drive. Hide the drive someplace secure.

PS. Obviously you're not keeping secrets from the wife ---HAHA!:D

---

### Post by suniyo on 2011-07-19
> **.psd said:**
> Ya, that would be the default workaround if linux was seriously so ridiculous as to not implement at least one method for password locking a file or folder. I'm hoping linux isn't that ridiculous so I came here to find out.

I'm not afraid of anyone hacking my files, I don't need *any* protection other than a simple password requirement. As I said, if I can enable and permanently become superuser, that is my preferred solution. I'm aware of all the dangers this implies.

unnecessary.. lol

---

### Post by al1x on 2011-09-10
You can compress your file which you don't want to be seen by others with zip and also password protect it.Even if you run ```
sudo unzip <file.zip>
``` it requires the passwd of the zip file to extract it.
To do this you just need to right click the file then click compress, choose zip and click the "Other options".

---

