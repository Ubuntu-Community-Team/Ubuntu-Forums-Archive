---
title: "Sharing my linux files with a windows machine."
date: 2006-04-09
forum: General Help
---

### Post by justinjstark on 2006-04-09
I want to be able to access my music on ubuntu with my roommates windows xp computer.  I was hoping it would be as simple as going into Shared Folders and adding the folder I want to share.  Unfortunately, I have not gotten this to work.  Anybody?

---

### Post by IYY on 2006-04-09
You need to install Samba. It's in the Ubuntu guide:

[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by nanotube on 2006-04-09
or even better (easier?) is to install an ssh server on your ubuntu, and then ssh in from the windows box. at least i find that ssh is my preferred method of sharing files. :)

---

### Post by justinjstark on 2006-04-10
[QUOTE=IYY]You need to install Samba. It's in the Ubuntu guide:

[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)[/QUOTE]

I have samba installed (but not smbfs...do I need it?).  When I go to Shared Folders settings, I have it set to the following options:

Share with: SMB
Name: Music
[x]Read only
[x]Allow browsing folder
General Windows sharing settings:
Host description: %h server (Samba, Ubuntu)
Domain / Workgroup: MSHOME
[o]Do not use WINS server

Yet windows cannot see it.

---

### Post by justinjstark on 2006-04-10
[QUOTE=nanotube]or even better (easier?) is to install an ssh server on your ubuntu, and then ssh in from the windows box. at least i find that ssh is my preferred method of sharing files. :)[/QUOTE]

But then I would have to scp the files over in order to play them, correct?  I'd like to be able to play them straight off of my computer without having to copy them at all.

---

### Post by nanotube on 2006-04-10
ehrm yea, but guess what - in order for your computer to play the files, it still has to get the data over the net from one comp onto the other. so either way, the file finds its way onto your computer. it just does so in a slightly more "transparent" way when you use samba :)

---

### Post by justinjstark on 2006-04-10
[QUOTE=nanotube]ehrm yea, but guess what - in order for your computer to play the files, it still has to get the data over the net from one comp onto the other. so either way, the file finds its way onto your computer. it just does so in a slightly more "transparent" way when you use samba :)[/QUOTE]

True, but it makes it easy to add files to a WMP playlist without hassle if I use samba.  ;)

---

### Post by IYY on 2006-04-10
> But then I would have to scp the files over in order to play them, correct? I'd like to be able to play them straight off of my computer without having to copy them at all.

Well, SSH can be used as a remote filesystem. Although in your case, I do think Samba is better.

---

### Post by nanotube on 2006-04-10
[QUOTE=blaksaga]True, but it makes it easy to add files to a WMP playlist without hassle if I use samba.  ;)[/QUOTE]

well, samba does have its advantages, from the windows pt of view. :) on gnome, an ssh connection can be mounted just like a drive.

---

### Post by JoeMetal on 2006-04-10
instead of SSH, you could always use SFTP.  I also use my Ubuntu box as a music cache and I access it from pretty much every where I go with SFTP.

---

### Post by Celerex on 2006-04-10
Yall are arguing semantics. SSH would be more secure but if security isn't a concern because you're mixing OS flavours I'd suggest sticking with the Samba method.

Samba is installed so configure it (/etc/samba/smb.conf) and add your users (smbpasswd -a <user>). This is all explained in the guide. You don't need SMBFS installed unless you're mounting remote shares on your ubuntu box. Your XP machine should (once things are setup) be able to simple type in a run box: \\ip_address\ and they'll be asked to authenticate. Use the account you added via smbpasswd and you should be off to teh races. Good luck.

---

### Post by Lars Skovbo on 2006-04-10
Thank you Celerex! Straight to the point, I like you ;)

---

### Post by justinjstark on 2006-04-10
[QUOTE=Celerex]Yall are arguing semantics. SSH would be more secure but if security isn't a concern because you're mixing OS flavours I'd suggest sticking with the Samba method.

Samba is installed so configure it (/etc/samba/smb.conf) and add your users (smbpasswd -a <user>). This is all explained in the guide. You don't need SMBFS installed unless you're mounting remote shares on your ubuntu box. Your XP machine should (once things are setup) be able to simple type in a run box: \\ip_address\ and they'll be asked to authenticate. Use the account you added via smbpasswd and you should be off to teh races. Good luck.[/QUOTE]

Alright, this works great.  Thank you.  I just didn't know how to access it...I figured windows would see it and add it to windows network but instead I had to add the share manually using the IP.

The only problem is that it allows me to access my entire home folder, not just my share folders.  :-?  I'm not sure whether or not I like this.

---

