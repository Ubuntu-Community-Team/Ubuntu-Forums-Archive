---
title: "Ubuntu One on a personal server"
date: 2009-11-18
forum: General Help
---

### Post by madu on 2009-11-18
Hello guys,

I started to use Ubuntu One just to see how it works and find it very useful.
What I want to know is, is there anyway I can install this on my server? rather than using the Ubuntu cloud? Or any toher alternative way.

What I need basically is to sync files. No need to share with anybody. I have a server running and a one desktop and a laptop which I use at home and uni. 

For example I work on a file at uni and want to continue on it at home. Usually I would copy it to a flash and take. But this is getting very cumbersome. Using a SVN would be an ideal solution but I think it's a bit of an ovekill and also a bit too complicated for my liking.

So if anybody have any idea or suggestion please drop them by here.

Cheers.

---

### Post by dcstar on 2009-11-18
[QUOTE=madu;8339608]Hello guys,

I started to use Ubuntu One just to see how it works and find it very useful.
What I want to know is, is there anyway I can install this on my server? rather than using the Ubuntu cloud? Or any toher alternative way.
....../QUOTE]

If you want the server you buy it - it is proprietary:

[https://wiki.ubuntu.com/UbuntuOne#Code%20and%20licensing](https://wiki.ubuntu.com/UbuntuOne#Code%20and%20licensing)

---

### Post by fragos on 2009-11-18
You can use NFS to provide file access to your local server and then run Unison to sync client with server. Here's what I do:

I use NFS between my Desktop and Laptop as my server. Both being on the same LAN. On the server there must be an /etc/exports with the following. Replace the fields in {} with your information. In my example I'm giving access to the entire home folder tree. There can be multiple entries giving more clients permission.

/home/{Laptop user} {Desktop hostname}.local(rw)

This allows the Desktop to access the home folder of the laptop. Prior to Ubuntu 8.04 you need to run "sudo exportfs -rv" for the system to read /etc/exports. New versions do this for you at boot.

On the Desktop create a folder to mount to. In my case I placed that folder in my home folder.

On the Desktop side I run

sudo mount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

To un-mount I run

sudo umount {Laptop hostname}.local:/home/{Laptop user} /home/{Desktop user}/{folder to mount to}

You can extrapolate what to do from this working example. I chose not to use fstab to mount and wrote a couple of bash scripts that supply the parameters to the mount and umount commands.

Configuration of Unison is very strait forward.

---

