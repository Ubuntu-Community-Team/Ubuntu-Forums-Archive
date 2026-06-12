---
title: "share files over a network"
date: 2010-09-13
forum: General Help
---

### Post by drdob on 2010-09-13
Dear all could you please help me? I have a complex problem! This is part of it.
Running Ubuntu 10.4 lts I wish to Share files and a printer over a network the network is run on my main computer running XP . but I no joy in the “share files over the network” box :system> preference >  personal file sharing .  “The box to share public files on network” is greyed out.
And the massage “this feature cannot be enabled because the required packages are not installed on your system” can anybody tell me just what packages I have to install. yours drdob

---

### Post by Naitsirhc Hsem on 2010-09-13
> Running Ubuntu 10.4 lts I wish to Share files and a printer over a network the network is run on my main computer running XP .
please fix this sentence, I can't understand what is on which computer.

thanks

---

### Post by sikander3786 on 2010-09-13
You need Samba for closs platform sharing.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

See this link for installing missing packages for Personal File Sharing.

[http://ubuntuforums.org/showthread.php?t=1473760](http://ubuntuforums.org/showthread.php?t=1473760)

---

### Post by pricetech on 2010-09-13
Samba.

In Synaptic; system-config-samba will install Samba as well as a GUI configuration tool, handy for those not cozy with the command line.

---

### Post by drdob on 2010-09-14
thank you all i have done all that .... and .. got nothing, i am going to check my main computer (the one i wish to share too) which is a windows XP would i have all this bother if it was Ubuntu?? ;)  yours drdob

---

### Post by sikander3786 on 2010-09-16
> **drdob said:**
> thank you all i have done all that .... and .. got nothing, i am going to check my main computer (the one i wish to share too) which is a windows XP would i have all this bother if it was Ubuntu?? ;)  yours drdob
Can you please be a little more specific about what you want to achieve? Do you want to share folders from your Ubuntu Box or they are shared from the Windows Box and you want to access them in Ubuntu?

And what did you try from the links posted above and what happened?

Regards.

---

### Post by drdob on 2010-09-16
i wish to just share folders between to to if it is posable. that is Ubuntu 10.4 to windows XP and back to Ubuntu if needed.
DrDob

---

### Post by Morbius1 on 2010-09-16
> but I no joy in the “share files over the network” box :system>  preference >  [COLOR=Blue]personal file sharing[/COLOR] .  “The box to share public files  on network” is greyed out.[COLOR=Blue]**Personal File Sharing**[/COLOR] is not Samba

If you want it to work you need to install the following packages:
```
apache2.2-bin
libapache2-mod-dnssd

```It sets up a small apache server and anounces it's one and only share at /home/username/Public using avahi.

For the money I think you're better off with samba as personal file sharing seems to be a very unstable.

---

### Post by sikander3786 on 2010-09-17
As Morbius1 suggested, Personal File Sharing is not Samba. And Samba is what is needed for cross platform sharing in Linux. Did you go through the links I provided in my 1st post?

---

### Post by HermanAB on 2010-09-17
Howdy,

There are many ways to share files between Windows and Linux.  In order of increasing difficulty:
1. FTP
2. SSH
3. NFS
5. Samba

1. You can install a FTP server on Windows and access it from Linux:
Download FileZilla Server on Windows and install it.  Use Nautilus file manager on Linux and use the File, Connect to Server function. (or use FileZilla client for Linux.)

2.  You can install a FTP server on Linux and access it from Windows using FileZilla Client:
Install proftpd of vsftpd on Linux.  Install FileSille Client on Windows.

3.  You can install a SSH server on Linux and access it from Windows using FileZilla Client:
Install ssh-server package on Linux.  Install FileZilla Client on Windows.

4. You can use Windows XP Server and access it from Linux using Nautilus file browser:
Right click on a folder in Windows and share it.  On Linux, run Nautilus and use File, Connect to Server to access the file share.

All of the above methods are almost trivial.

5. You can install Windows Services for UNIX on Windows (a free download from MS), install a NFS server in Linux and access it from Windows:
Download and install Windows services for UNIX
Install NFS Server on Linux.  Configure the file /etc/exports (a one liner).

The above is not particularly difficult.

6. You can install a Samba server on Linux and access it from Windows mapping a drive letter to it.  This is very difficult.  The Ubuntu wizard usually works.  If the wizard doesn't work, then you may have to spend a few weeks reading the Samba book (about 2 inches thick) plus many hours of happy debugging.

A NFS server has ONE single lonely line of configuration.  Samba has hundreds.  You do the math on the number of things that can go wrong with Samba.

I gave up with Samba many years ago as a waste of time.  Yes, I have used it a lot and I can make it work if I want to, but NFS is a much better solution. If I just want a quick way to transfer files, I use FTP (FileZilla or vsftp).  If I want a secure way to transfer files, I use SSH and FileZilla.

Hope that helps.

---

### Post by stinkeye on 2010-09-17
There is a simple tutorial on file sharing with Samba here....
[**_[COLOR="DarkRed"]http://www.ghacks.net/2010/02/23/easy-folder-sharing-in-gnome/[/COLOR]_**]("http://www.ghacks.net/2010/02/23/easy-folder-sharing-in-gnome/")

---

### Post by drdob on 2010-09-18
thank you all i think i have a handal on it now. i will have a beer and go do it. yours drdob

---

### Post by pricetech on 2010-09-20
> **HermanAB said:**
> You can install a Samba server on Linux and access it from Windows mapping a drive letter to it.  This is very difficult.

I hope you're just kidding.  Samba is a piece of cake to set up and make work.  You can make it more difficult if you want to, but I've never been a glutton for punishment myself.

I did not know that Filezilla supports SSH though.  Glad you mentioned that.

---

