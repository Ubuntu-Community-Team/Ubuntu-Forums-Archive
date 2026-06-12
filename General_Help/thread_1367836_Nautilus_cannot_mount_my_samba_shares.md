---
title: "Nautilus cannot mount my samba shares?"
date: 2009-12-30
forum: General Help
---

### Post by Nooki on 2009-12-30
Hi everyone!

I've been fighting with Samba shares lately, without success. 

If I use the right click approach, and sets guest ok and write access, I obtain a usershare which can be seen with smbclient (such as : [FONT="Courier New"]smbclient -L myusername-desktop[/FONT]). I can even explore the contents of my share using smbclient : [FONT="Courier New"]smbclient //myusername-desktop/myshare[/FONT], in a terminal. 

However, I must supply my login password, or smbclient will return [FONT="Courier New"]session setup failed: NT_STATUS_LOGON_FAILURE [/FONT]

If I try to browse my share with Nautilus, in Places->Network, I can see my shared folder, but if I double click on it, I get an error, which says something along the lines : Unable to mount the Windows share. The shared folder has executable and writable rights. Trying to mount it using [FONT="Courier New"]gvfs-mount smb://myusername-desktop/myshare [/FONT] returns a similar error message.

Samba is installed and running, with the default [FONT="Courier New"]/etc/samba/smb.conf[/FONT] file. I've tried playing with it, setting [FONT="Courier New"]security=share[/FONT] instead of [FONT="Courier New"]security=user[/FONT], but then it would just get worse. Also tried manually creating the shares using the [FONT="Courier New"]smb.conf[/FONT] and obtained the same results.

Another computer here has Ubuntu 9.04 instead of my 9.10, and the shares works great, using the usershare approach (right click) and not messing around at all. The only difference I was able to find is that on Ubuntu 9.04, the shares created truly don't care about passwords. Maybe this cause a problem with Nautilus. Shouldn't it asks me for a password when I type [FONT="Courier New"]smb://myusername/myshare[/FONT] in Nautilus address bar then?

Q1 : Does some of you experience the same problems using samba shares on Ubuntu 9.10?

Q2 : If it works for you, how did you do it? Do you have any hints which could help me debug this mess? What I want is a passwordless access to Samba shares using Nautilus.

Thank you for taking the time to read this long post, and happy new year!

---

