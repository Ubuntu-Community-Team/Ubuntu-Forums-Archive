---
title: "Windows Shares"
date: 2012-04-30
forum: General Help
---

### Post by Ubun2to on 2012-04-30
My dad has a server running Windows Server 2008, and they want me to switch to Ubuntu, and one of the things they want to make sure of is that they can access their network drives. I told my dad to wipe the server and install Ubuntu Server, but he can't because he has lots of program data he needs for his work.
The problem is, my dad doesn't have Active Directory configured on the server, so we are using a Workgroup, and not a Domain (I can't get AD on that server to work to save my life). So, when I went into the mount share box, I can't enter a Workgroup-just a Domain.
I tried joining a Workgroup via a Samba tutorial I read [here]("http://www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows"), but that didn't help.
Any way I can mount a Windows share that's on a Workgroup?

---

### Post by JRV on 2012-04-30
From the command line:
```
nautilus smb://Windows_Hostname/Windows_Sharename
```

From the GUI:

Click on the desktop so global menu looks at desktop.
Click File=>Connect to Server.
Change Type: to Windows Share.
Server = Windows_Hostname.
Share = Windows_Sharename.
Leave Folder where it is and Domain Name blank.
Enter the User Name and Password.
Click Connect.

---

### Post by uylug on 2012-04-30
I don't think it really matters what you write in the boxes ( except of course the "username" and "password" fields).

Running the command suggested by Ubun2to should work for you.

---

