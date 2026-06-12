---
title: "Netware Shares"
date: 2006-06-06
forum: General Help
---

### Post by emarcellus on 2006-06-06
I am running 6.06.
I have searched the forums but cant quite seem to find a good example.
I am trying to mount a novell share and I do not seem to be having much luck.
Has anyone done this under 6.06?

Thanks for any and all help.

Ed

---

### Post by g-a-c on 2006-06-09
Once you've installed ncpfs (which is in universe or multiverse, I forget which) you can use the ncplogin and ncpmap commands to authenticate to NDS and map drives.

I've used something like this in the past (not specifically on Ubuntu, mainly Gentoo and CentOS):

```
#!/bin/bash

if [ ! -d ~/gdrive ]; then
	mkdir ~/gdrive
	chmod 700 ~/gdrive
fi

if [ ! -d ~/ydrive ]; then
	mkdir ~/ydrive
	chmod 700 ~/ydrive
fi

if [ ! -e $1 ]; then
	NDSUSER=$USER
else
	NDSUSER=$1	
fi

if [ ! -e $2]; then
	CONTEXT=$2
else
	CONTEXT=users.el
fi

ncplogout -a > /dev/null
echo "Enter NDS password for $NDSUSER.$CONTEXT"
read -s NDSPASS

ncplogin -S SERVER1 -A server1.domain -U .$NDSUSER.$CONTEXT -P $NDSPASS -o tcp || ncplogin -S SERVER2 -A server2.domain -U .$NDSUSER.$CONTEXT -P $NDSPASS -o tcp || ncplogin -S SERVER3 -A server3.domain -U .$NDSUSER.$CONTEXT -P $NDSPASS -o tcp || echo "Couldn't authenticate to any NDS server, aborting..."

ncpmap -S SERVER1 -A server1.domain -V VOL2 -R users/$NDSUSER ~/gdrive || ncpmap -S SERVER2 -A server2.domain -V VOL2 -R users/$NDSUSER ~/gdrive || ncpmap -S SERVER3 -A server3.domain -V VOL2 -R users/$NDSUSER ~/gdrive || echo "Couldn't map to your G: drive, aborting..."

ncpmap -S SERVER1 -A server1.domain -V VOL1 -R shared ~/ydrive

unset NDSPASS
```

This is incredibly messy, I know, but it works for me! Since this was only for use by a couple of people, I didn't try and do anything complicated like reading their home directory from NDS, it just tries to mount from our 3 servers sequentially, as each user has a homedir on exactly one of them. I'm sure you could change it to your own needs...

Hope this helps!

---

### Post by renatosilva on 2007-04-25
I'm currently using a modification of this script to map my netware drives, but I would like to integrate Netware login with GDM, so that when I'm prompted to log-in  into GNOME then it does also in Netware. 

A simple way that I was thinking is that if would exist a way to call the script passing the typed login and password from GDM login (this requires the local Linux account/password being the same as remote Netware, but it's still good for me).

Does anyone know??

---

### Post by renatosilva on 2007-04-25
Up...

---

### Post by renatosilva on 2007-10-10
Up...

---

### Post by XeroxGUI on 2007-11-03
I am absolutely no help at all to this subject, but a new lab I manage in my university is (going to have) all Ubuntu/Xubuntu machines, and the school uses Novell 4 servers. 
 
I have set up Windows clients for Novell, but a similar linux client would be HUGE for me, especially if it can look almost identical to win client SP4, with the school licence agreement, workstation only, and everything. I am negotiating with Novell for some source so maybe I can (C++ or Java) my own client GUI for it, but does anyone know of a tmp fix?:confused:

---

### Post by mahousaru on 2007-11-03
You can archive single sign on using pam-script (its listed on the Novell site, just checking if I can link to Novell before getting slapped).

pam-script takes the auth details and pipe them into other commands.  So you can get it to use the same username and password to mount the ncpfs shares.  btw Netware especially OES Linux should allow you to use other network file systems so don't feel locked to ncpfs.

---

