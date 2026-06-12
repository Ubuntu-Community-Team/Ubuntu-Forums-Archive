---
title: "Remote Desktop Client"
date: 2011-05-24
forum: General Help
---

### Post by RoyVas on 2011-05-24
Hi 
First post to this forum hope you guys can assist.

I am running Ubuntu 10.10 and use it to connect to, and work on several Windows 2008 servers. I have no problems connecting (in fact much faster than from windows machine)I do have a problem with clipboard though I am able to copy text from the server to the Ubuntu box but not back the other way.

The big issue however is that I am unable to copy files in either direction. I frequently need to copy pdf files from the local machine to the server and sometimes back the other way. This is possible with copy and paste in both directions when using a windows box on the same network as the Ubuntu machine. 

I am using RDPv5 in the TS Client and have connected my local disc checked.

Any suggestions gratefully received 
Thank you for taking the time to read this

---

### Post by smurphy_it on 2011-05-24
You could setup an OpenSSH server.  Then just use copy them from one machine to the other.

On the windows machine, use putty's scp command, or grab a sftp windows client.  Connect to your linux box and download the file(s).

Using scp you can copy from the linux box or to the linux box.

sudo apt-get install openssh-server

You might want to edit /etc/ssh/ssh_config and change the following line so root can't login.

```
sudo nano /etc/ssh/sshd_config
```
and look for PermitRootLogin line.
Make sure it reads "PermitRootLogin no"

then re-start the sshd daemon.
```
sudo service ssh restart
```

---

### Post by RoyVas on 2011-05-24
Hi smurphy_it
Thanks for your reply, if I understand correctly your suggesting linking via FTP which I am aware I can do, but I am really hoping to be able to replicate the same facility I currently use if at all possible.

also without doing anything to the configuration of the servers.

---

### Post by smurphy_it on 2011-05-24
Actually I was referring to using SFTP, not ftp.  As sftp is a daemon of OpenSSH, and uses encryption.  Where-as FTP is plain text, and one can catch your login name & password, not to mention do a mitm attack.

If you don't want to modify any of the servers, then you are limiting your options.

If there is no worry on the type of data you are transferring, you could use FTP on each respective platform/machine and sent the relevant files to a dump site (or email them if small enough).

If the data is sensitive in any way, then you would want to encrypt it first.  Multiple ways of doing that.  Zip password encryption, gnupg, etc.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try Teamview 6

---

### Post by RoyVas on 2011-05-26
Hi 
Thanks again for your reply's
Its not that I dont want to modify the servers,it is that I cant as although I have admin rights I also have several hundred users on theses machines and cant run the risk of disruption if I get it wrong.

Will try teamviewer but if it is similar to the windows offering not sure it will suffice.

Thank you both again for your assistance

---

### Post by RoyVas on 2011-05-26
In fact can only find a windows version !

---

### Post by e79 on 2011-05-26
More simple than all of the above (sorry guys :)) ...install _Remmina_ from the Ubuntu Software Center, I am personally using it to connect to about 10 different Windows Server and can copy files in both direction on all of em  :)

hope this helps

---

### Post by RoyVas on 2011-05-26
Hi e79
I certainly can now copy text in either direction :)thanks which is a distinct improvement but am still unable to copy files in either direction.

I am using the RPD windows terminal service is there a setting i am missing perhaps ?

---

### Post by e79 on 2011-05-26
Did you checked the 'Share Folder' and specified one at the bottom of the first config window ? This is where I specify which folder on my PC i want to 'share' with the server; so when navigating 'Computer' from the server, I see it and can copy/paste from/to it.

Hope this helps  :D

---

### Post by RoyVas on 2011-05-27
e79 
Thank you that has solved my problem, works perfectly much appreciated.

---

### Post by e79 on 2011-05-27
The pleasure is all mine  :p
 
Best Regards

---

### Post by Jaksis on 2011-06-17
Ahh, i have problem, that i can't just copy/paste text from remote win2008 to ubuntu 11.04. And from ubuntu to win2008 too...

Few days ago terminal server client work good, can copy/paste, but now it likes something happens, and cant copy/paste...

But this is on all my remote desktop clients: remmina, TSC, rdesktop

---

### Post by e79 on 2011-06-17
Jaksis,
 
In the future, please do not highjack a thread that was already [SOLVED]. Open you own thread.
 
As for your problem of copy/paste; I would suggest to look at your Group Policy (whether in a domain or not) to make sure the 'ClipBoard Redirection' is at 'Not Configured' as shown in the attached picture (my picture shows it as 'Enabled', preventing all copy/paste and such).
 
Tell us if it helps.

---

