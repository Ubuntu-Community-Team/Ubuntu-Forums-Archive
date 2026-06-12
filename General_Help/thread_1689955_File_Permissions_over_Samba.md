---
title: "File Permissions over Samba"
date: 2011-02-17
forum: General Help
---

### Post by dazman19 on 2011-02-17
Hi

I have a problem with file permissions over samba.

I am running a web server, and this web server needs to be able to delete a file. The php code is correct, because it works on other sites. 
The php code is failing when it deletes a file because it is being ran as the www-data user. And the permissions on the files that are created on the share are as follows:

ns$ ls -l
-rwxr-xr-x 1 root root 129628 Feb  6 08:16 20110206071748532.pdf

This directory is mounted on:
/var/www/files/23982dbb7a454425ce17a22bedc00776/scanned/AEC_Scans

This is done with the /etc/fstab file:

//192.168.58.2/Scans /var/www/files/23982dbb7a454425ce17a22bedc00776/scanned    smbfs username=administrator,password=somepass       0

my web server read the files and does everything it needs to, but it doesnt have permission to delete the files and I DO NOT want to make the web server user run as a root user.

here is my smb.conf file for that share:

[files]
        comment = Access Share for Eftpos/Scans
        path = /var/www/files/23982dbb7a454425ce17a22bedc00776
        browseable = yes
        writable = yes
        guest ok = yes
        force user = www-data
        force group = www-data
        create mask 0777
        read list = www-data
        write list = www-data

I still have no luck. chmod or chown doesnt work either heres a verbose call to chown:

chown -Rv www-data AEC_Scans/

changed ownership of `AEC_Scans/20110217153509834.pdf' to www-data
changed ownership of `AEC_Scans/20110217153515921.pdf' to www-data
changed ownership of `AEC_Scans/20110217153522097.pdf' to www-data
changed ownership of `AEC_Scans/20110217153555364.pdf' to www-data
changed ownership of `AEC_Scans/Thumbs.db' to www-data
changed ownership of `AEC_Scans/' to www-data
user@host:/var/www/files/23982dbb7a454425ce17a22bedc00776/scanned$ 

then an ls -l on the scans folder after the chown:

-rwxr-xr-x 1 root root 661619 Feb 17 16:33 20110217153503682.pdf
-rwxr-xr-x 1 root root 128783 Feb 17 16:34 20110217153509834.pdf
-rwxr-xr-x 1 root root 137512 Feb 17 16:34 20110217153515921.pdf
-rwxr-xr-x 1 root root 131491 Feb 17 16:34 20110217153522097.pdf
-rwxr-xr-x 1 root root 836070 Feb 17 16:34 20110217153555364.pdf
-rwxr-xr-x 1 root root  30720 Feb 11 07:42 Thumbs.db

please help

---

### Post by WorMzy on 2011-02-17
I'm not sure what fstab options smbfs supports, but you could try adding uid=33,gid=33,umask=002 and see if it helps.



* Change 33 to the uid/gid of your www-data user if yours uses a different one.

---

### Post by dazman19 on 2011-02-17
do I add this to my fstab mount call? Or do I add it to my smb.conf?

e.g.
I have checked my uid/gid for www-data and it is 33.


//192.168.58.2/Scans /var/www/files/23982dbb7a454425ce17a22bedc00776/scanned    smbfs username=administrator,password=Xsw26yhn110,uid=33,gid=33,umask=002       0           0

---

### Post by WorMzy on 2011-02-17
Sorry, I should have been more clear there, but you figured it out yourself. Add it to the fstab entry, in the options. Make sure that the list of options is only comma separated (no spaces/tabs allowed).

You have a space after the uid value, you'll need to remove it or it won't work (and may even cause problems)

```
//192.168.58.2/Scans /var/www/files/23982dbb7a454425ce17a22bedc00776/scanned smbfs username=administrator,password=Xsw26yhn110,uid=33,gid=33,umask=002 0 0
```

---

### Post by dazman19 on 2011-02-17
thanks so much for your help wormzy.

One other thing, Samba starts AFTER my /etc/fstab file tries to mount so it fails in the boot and i need to run mount -a manually once i log in. 

If i put noauto i guess it will load faster, but what do you think is the best way to mount this on startup. Its actually a virtual machine hosting a web server.

---

### Post by WorMzy on 2011-02-17
I've never used network drives myself, so I'm not really the best person to ask here, but I found [a post on another forum]("http://www.linuxquestions.org/questions/linux-server-73/mount-samba-share-at-boot-with-fstab-667392/") which suggested using cifs instead of smbfs, and adding "_netdev" to the options. Apparently that makes mountall background the task of mounting the network share if it's not available during the boot up phase.

Maybe this will help you.

---

### Post by SeijiSensei on 2011-02-17
> One other thing, Samba starts AFTER my /etc/fstab file tries to mount so it fails in the boot and i need to run mount -a manually once i log in.

Are you connecting to the network at boot, or do you connect from the desktop?  On servers, you almost always want to have the network start up at boot to make sure things work without intervention if there's a reboot, etc.  In fact you probably want it to have a [static address]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html").

I just throw an smbmount command in /etc/rc.local to mount remote SMB/CIFS shares since it will happen at the end of the boot sequence when the network is up.

You actually don't need to be running Samba on a machine if you only want it to be a client mounting remote shares.  You just need to mount the shares with smbmount or via the cifs type in /etc/fstab.

---

