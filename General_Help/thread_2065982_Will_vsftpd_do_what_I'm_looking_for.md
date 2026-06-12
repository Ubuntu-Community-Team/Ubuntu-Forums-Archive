---
title: "Will vsftpd do what I'm looking for?"
date: 2012-10-03
forum: General Help
---

### Post by watson524 on 2012-10-03
Hi all,

I've been reading through various posts/guides on vsftpd (most recently this one [http://ubuntuforums.org/showthread.php?t=518293&page=6](http://ubuntuforums.org/showthread.php?t=518293&page=6)) and I am not clear on something.

In my windows world, I had an FTP server set up where users could log in from the outside and get access to various folders (mainly mapped network drives). Can that be done with VSFTPD? I have a few network drives that I want to give certain people outside access to. I know I have to forward ports on my router and all but before I install vsftpd, I'm confused on what it can do. I get that the user names have to have an account on the linux box and I can give them a fake shell, but how do I get them to see say \media\2tbext\directory1\directory2? And can I give them access to multiple areas?

thanks!

---

### Post by Lars Noodén on 2012-10-03
You might consider leaving FTP behind as a legacy of Windows

[list]
[*] [http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely](http://www.openlogic.com/wazi/bid/188103/Stop-Using-FTP-How-to-Transfer-Files-Securely)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

If you want to provide a secure way to transfer files, you can use SFTP instead.  There are SFTP clients built into both Nautilus and Dolpin, in addition to the text-based SFTP client on your system.  In Dolphin or Nautilus, it is enough to press ctrl-L and then enter the URI, sftp://xx.yy.zz.aa/  

To set up an SFTP server, all you need is the package OpenSSH-server.  If you have that, you already have SFTP up and running.  If you want to chroot SFTP users to specific directories, that is fairly easy too.

---

### Post by watson524 on 2012-10-03
Thanks for the recommendation, sounds like a good idea based on the links you provided and your input.

Do you know if users can access using internet explorer or chrome on windows machines or do they need to install a client?

> **Lars Noodén said:**
> 
To set up an SFTP server, all you need is the package OpenSSH-server.  If you have that, you already have SFTP up and running.  If you want to chroot SFTP users to specific directories, that is fairly easy too.

Also I'm pretty new at all this. I searched the software center for ssh and server (separately) and nothing called OpenSSH-server shows up. I don't know if I need a different repository and how to do all that or if I'm just missing something.

---

### Post by watson524 on 2012-10-03
Actually did it through command line and that seemed to work so I'll try to figure out the setup

sudo apt-get install openssh-server

---

### Post by Lars Noodén on 2012-10-03
Yes, that's an easy way to install it.  

It's in the main repository: [http://packages.ubuntu.com/precise/openssh-server](http://packages.ubuntu.com/precise/openssh-server)

It's configured to give you SFTP out of the box, no changes needed.

---

### Post by watson524 on 2012-10-03
I have it running and on my windows machine I installed winscp and am able to connect to /home/michele with no problems. I also created an account on the machine for my friend and she can log in and see /home/shannon with no issues but my issue is, I want her to see /media/2tbext/directory1/directory1 (with read only permissions) and don't know how to do that

thanks in advance!

---

### Post by Lars Noodén on 2012-10-03
I'm not sure how winscp would work but in Nautilus you can put in the path as part of the URL when you connect.  Something like this:

sftp://watson524@*xx.yy.zz.aa*/media/2tbext/directory1/directory1

Or you can click on the small triangle on the path above the folders where your user name is.  That will open up a small navigation bar and you can walk your  way up to the top from /home/watson524 and then back down again into /media/2tbext/directory1/directory1  See the snapshot in the attachment.  The red arrow shows where you can click to expand the navigation path.

---

### Post by watson524 on 2012-10-03
Ok that's what I have to figure out because people coming in from the outside are only using windows and winscp... Seems by default it only gives access to her home directory /home/shannon and I can't even write to that (as the admin, which I thought was odd) to drop files there for her. but that wouldn't even be ideal, ideally I'd be able to set her home directory as /media/2tbext/blah/blah or at least let her be able to change to it

---

### Post by windscape on 2012-10-03
Hi,

I think WinSCP will follow symbolic links by default so as long as the permissions on the /media/2tbext directory are correct, you should be able to create a symbolic link in /home/watson524 to /media/2tbext and that way they can just double-click on that folder in WinSCP after they login and it should take them to /media/2tbext.

---

