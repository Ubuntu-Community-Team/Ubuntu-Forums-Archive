---
title: "Karmic Koala Networking Problem"
date: 2009-11-04
forum: General Help
---

### Post by ozguitarplayer on 2009-11-04
Hi,
I have set up on Debian Lenny, 2xHardy Heron and 1xJunty Jackalope a peer to peer network.
I use; 
ssh and sshfs
wicd instead of Network Manager

and have edited /etc/hosts to list ip and host name.

It has always been a very simple reliable way for me to network and I have gone through the process a many of times with new installs.

After installing Karmic Koala on another partition and using the same setup I cannot connect from the other computers to Karmic Koala. 
I get < Cannot display location "sftp://slvko/" >

I can connect from Karmic Koala to the other computers.

Has anyone had the same problem?
Any advice is appreciated.

---

### Post by Peter09 on 2009-11-04
First try using an IP address instead of the machine name - does that work?

Also use the -v switch to get a better debug output.

---

### Post by grandtoubab on 2009-11-04
maybe have a look at
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Networking)

---

### Post by ozguitarplayer on 2009-11-04
Thanks for that,
I have tried IP address instead of machine name, it gets the same result.
What is the -v switch and how do I use it?

---

### Post by Peter09 on 2009-11-04
Try

```
ssh -v -X <your username>@<machine name> xterm
```
you should get a request for a password followed by a remote terminal.

---

### Post by soapBAR2 on 2009-11-04
You could always try SAMBA/CIFS. Just

On the host machine:
```
sudo apt-get install smbfs
sudo nano /etc/samba/smb.conf

```
Add a section at the bottom
> [ShareName]
path = /path/to/share folder
comment = Comment
public = yes
read only = no
guest ok = yes
valid users = user1 user2 user3
write list = user1
create mask = 0555


(Remembering that if you don't want some of those options, just leave them out)

(still on the host:)
```
sudo /etc/init.d/samba restart
```

Then (on the client), open /etc/fstab, and add the following line
> //Host/Sharename /mnt/hostshare cifs noperm,user=username,password=password 0 0 

Then

```
sudo mount -a
```

And you're done.

---

### Post by ozguitarplayer on 2009-11-04
Thanks again,
Using > ssh -v -X <your username>@<machine name> xterm
doesn't connect me to the Karmic Koala computer, it seems there are password issues that I have to resolve.

I haven't tried samba/CIFS as I didn't think I need to if I'm using ssh, is this correct?

---

### Post by Peter09 on 2009-11-05
If ssh will not connect then Samba will not resolve that. You will need to sort your passwords out, as you suggested.

---

### Post by ozguitarplayer on 2009-11-05
Solved, I hadn't deleted the entries in /.ssh/know_hosts file for the install proir to the Karmic Koala install, once I deleted them the file was updated automaticly with the new when I sucessfully connected to Karmic Koala.
Thanks all, if it wasn't for your advice I don't think I would have thought of that particular file.

---

