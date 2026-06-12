---
title: "Samba, Windows, and Permission"
date: 2009-10-24
forum: General Help
---

### Post by Tyrsius on 2009-10-24
I am using Ubuntu as a media server for a number of Windows machines and and a 360. I have ushare set up and video streams to the 360 just fine. Samba is set up and the folder is shared, which allows Windows users to copy files to the server.

The only problem is the folders/files added by windows users have very odd permissions. When viewed from the windows machine, they are marked as read-only and this cannot be unchecked, when viewed from the linux box they have no owner, and cannot be modified. In this state, the 360 will not read the folders.

If I sudo nautilus I can change the permissions, but doing this every time media is added is a great hassle. Is there any way to set the permissions of all files, even newly added ones, so they everyone has read/write access?

Edit: As a side-note. Whenever I restart ushare, I get a the following:
* Stopping uShare UPnP A/V & DLNA Media Server: ushare            [OK]
* Starting uShare UPnP A/V & DLNA Media Server: ushare 
/etc/ushare.conf: 6: Media: not found                             [OK]

What does this mean, and how can I fix it?

---

### Post by mdlueck on 2009-10-24
Did you set up Samba as a PDC, or non-PDC share mode?

To get workable file perms on the Samba shares from Linux workstations using mount.cifs to map the drives, I added to the server smb.conf

# Added as a test to get correct perms on the Samba server
   unix extensions = no

Otherwise the Linux client OS perms were taking presidence over the real perms on the server.

Then to correct the perms that the Linux clients were seeing on files on the Samba server, I had to pass the following args to mount.cifs

-o credentials=/home/mdlueck/.smbcredentials,uid=mdlueck,gid=mdlueck,dir_mode=0777,file_mode=0666

In each of my shares on the Samba PDC, I have the following entries:

   create mask = 0666
   directory mask = 0777

One last tip, I have prepared (a while ago) a Samba PDC for Windows Clients presentation which may be found here:

Samba 3 PDC for Windows Clients and Samba 3 Book Review
[http://www.lueckdatasystems.com/pub/presentations/iccm2007.pdf](http://www.lueckdatasystems.com/pub/presentations/iccm2007.pdf)

I hope that is of help to solving your challenge.

Sincerely,
Michael Lueck
Lueck Data Systems
[http://www.lueckdatasystems.com/](http://www.lueckdatasystems.com/)

---

### Post by Tyrsius on 2009-10-24
I hit google before I posted this, and did some research, but couldn't find enough to make sense of a few things. I apologize for my noobishness, but you'll have to dumb/break it down a bit for me. Still fairly new to Ubuntu/Linux.


> **mdlueck said:**
> Did you set up Samba as a PDC, or non-PDC share mode?

I don't know what PDC is (tried google, but it stands for many things) and I am not sure how to check if I have it setup or not.

> **mdlueck said:**
> 
To get workable file perms on the Samba shares from Linux workstations using mount.cifs to map the drives, I added to the server smb.conf

# Added as a test to get correct perms on the Samba server
   unix extensions = no

Otherwise the Linux client OS perms were taking presidence over the real perms on the server.

Then to correct the perms that the Linux clients were seeing on files on the Samba server, I had to pass the following args to mount.cifs

-o credentials=/home/mdlueck/.smbcredentials,uid=mdlueck,gid=mdlueck,dir_mode=0777,file_mode=0666

In each of my shares on the Samba PDC, I have the following entries:

   create mask = 0666
   directory mask = 0777

Searched Ubuntu for a mount.cifs file, couldn't find it. I'm assuming it's a setting in Ubuntu, but I don't know how to pass arguments to it. I have no clue where to put those PDC mask entries, nor what they do.

> **mdlueck said:**
> 
Samba 3 PDC for Windows Clients and Samba 3 Book Review
[http://www.lueckdatasystems.com/pub/presentations/iccm2007.pdf](http://www.lueckdatasystems.com/pub/presentations/iccm2007.pdf)

I hope that is of help to solving your challenge.

Sincerely,
Michael Lueck
Lueck Data Systems
[http://www.lueckdatasystems.com/](http://www.lueckdatasystems.com/)

That presentation looks like it handles a lot more than what I need to do, but I will go over it a few more times. Again, sorry for my lack of knowledge in this area, I have only barely played with Samba/ushare, and only succeeded it getting as far as I did with very detailed guides.

---

### Post by mdlueck on 2009-10-25
> **Tyrsius said:**
> I don't know what PDC is (tried google, but it stands for many things) and I am not sure how to check if I have it setup or not.

PDC stands for Primary Domain Controller.

[http://en.wikipedia.org/wiki/Primary_Domain_Controller](http://en.wikipedia.org/wiki/Primary_Domain_Controller)

> **Tyrsius said:**
> Searched Ubuntu for a mount.cifs file, couldn't find it. I'm assuming it's a setting in Ubuntu, but I don't know how to pass arguments to it. I have no clue where to put those PDC mask entries, nor what they do.

Ubuntu, like Debian, packages that file in a package named SMBFS. Like I explained, I use it to accomplish for Linux clients the equivalent to "drive mappings" with logon scripts. That is one of the official Samba packages within Ubuntu / Debian.

I had no idea what OS your client was in your case, so tried to pull out content appropriate for "\" and "/" OS's alike! ;-)

After much time, I have arrived at a configuration which works well for both OS client types.

Sincerely,

---

