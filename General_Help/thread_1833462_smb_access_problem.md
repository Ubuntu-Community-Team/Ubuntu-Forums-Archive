---
title: "smb access problem"
date: 2011-08-26
forum: General Help
---

### Post by winjeel on 2011-08-26
I have been using an external hard drive on my home network for about a year. The "LAN drive" has worked with 10.10, 11.04,  Windows XP (dual boot computer), and even with my Dell Mini10 running 10.04 connecting via wifi, and works with a third computer running Windows Vista. The address that has always been used is smb://landisk/disk/ still works on the Dell Mini, the Windows Vista computer, and my XP but now not 11.04.

The problem is that now, quite suddenly, accessing the drive doesn't work on my 11.04. The only change there had been is switching from the new menu system with pop-out side bar to the classic menu bar system. Otherwise, there had been no updates so no other reason for accessing the LAN drive to suddenly stop. I have run updates, but still no access, and not even Firefox can access it anymore.

Just to reiterate, the other computers can connect to it fine, and so can this dualboot-computer when running XP. How can I regain access to my LAN drive via 11.04? Also, I really don't like that new menu system, please avoid suggesting that I go back to it. And please refrain from making comments about how I should quit Windows.

---

### Post by Wayne_V on 2011-08-26
possibly there are some funky dependencies where smbfs got removed with the new menu system???

Try in a terminal and see if you get any errors:


$ smbclient -Llandisk

$ sudo mkdir /tmpmnt
$ sudo mount -t cifs //landisk/disk  /tmpmnt

you may need:

$ sudo mount -t cifs //landisk/disk -o user=xxx,password=yyy /tmpmnt 

depending on your config.  see 'man smbmount' for more options.   If there are errors you should see something in /var/log/samba.   Also check the log files on the server if there are any.

---

### Post by winjeel on 2011-08-26
Thanks for the quick response. This is what I got. I have no idea what it means, but it doesn't seem promising...

> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
andrew@andrew-Latitude-D520:~$ 


There is no password required, unless admin functions are being performed on the disk.

---

### Post by Wayne_V on 2011-08-26
what is the output of 'smbclient -Llandisk' ?

what was the exact command you used.  If you accept anonymous mounts, this command should work:

$ sudo mount -t cifs //landdisk/disk -o user=anonymous /tmpmnt

just hit return if it prompts you for a password.

---

### Post by winjeel on 2011-08-26
> **Wayne_V said:**
> what is the output of 'smbclient -Llandisk' ?

what was the exact command you used.  If you accept anonymous mounts, this command should work:

$ sudo mount -t cifs //landdisk/disk -o user=anonymous /tmpmnt

just hit return if it prompts you for a password.

first smbclient -landisk
> Usage: smbclient [-?EgBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-p|--port=PORT] [-g|--grepable] [-B|--browse]
        [-d|--debuglevel=DEBUGLEVEL] [-s|--configfile=CONFIGFILE]
        [-l|--log-basename=LOGFILEBASE] [-V|--version]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] service <password>


and then "$ sudo mount -t cifs //landdisk/disk -o user=anonymous /tmpmnt"
> [sudo] password for andrew: 
mount: wrong fs type, bad option, bad superblock on //landisk/disk,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



---

### Post by Wayne_V on 2011-08-26
for smbclient, you need the -L<netbios name>, so "smbclient -Llandisk", not just "smbclient -landisk"

did smbfs get uninstalled somehow:

dpkg --list | grep smbfs
or 
which mount.cifs

I would make sure everything is still installed:

sudo apt-get install samba smbclient smbfs samba-tools

---

### Post by winjeel on 2011-08-26
First I tried to (re)install smb and still doesn't connect. then I tried these and got these results:

> andrew@andrew-Latitude-D520:~$ which mount.cifs
/sbin/mount.cifs
andrew@andrew-Latitude-D520:~$ dpkf --list | grep smbfs
No command 'dpkf' found, did you mean:
 Command 'dpkg' from package 'dpkg' (main)
dpkf: command not found
andrew@andrew-Latitude-D520:~$ 


---

### Post by Wayne_V on 2011-08-26
yes, that is dpkg, not dpkf.  Please send the output of:

$ smbclient -Llandisk -Uanonymous

$ dpkg --list | grep -i -e smb -e samba

---

### Post by winjeel on 2011-08-30
> **Wayne_V said:**
> yes, that is dpkg, not dpkf.  Please send the output of:

$ smbclient -Llandisk -Uanonymous

$ dpkg --list | grep -i -e smb -e samba

Here...

> andrew@andrew-Latitude-D520:~$ smbclient -landisk -Uanonymous
Usage: smbclient [-?EgBVNkPeC] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-m|--max-protocol=LEVEL] [-T|--tar=<c|x>IXFqgbNan]
        [-D|--directory=DIR] [-c|--command=STRING] [-b|--send-buffer=BYTES]
        [-p|--port=PORT] [-g|--grepable] [-B|--browse]
        [-d|--debuglevel=DEBUGLEVEL] [-s|--configfile=CONFIGFILE]
        [-l|--log-basename=LOGFILEBASE] [-V|--version]
        [-O|--socket-options=SOCKETOPTIONS] [-n|--netbiosname=NETBIOSNAME]
        [-W|--workgroup=WORKGROUP] [-i|--scope=SCOPE] [-U|--user=USERNAME]
        [-N|--no-pass] [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        [-C|--use-ccache] service <password>
andrew@andrew-Latitude-D520:~$ dpkg --list | grep -i -e smb -e samba
ii  libsmbclient                          2:3.5.8~dfsg-1ubuntu2.3                    shared library for communication with SMB/CIFS servers
ii  libwbclient0                          2:3.5.8~dfsg-1ubuntu2.3                    Samba winbind client library
ii  nautilus-share                        0.7.2-14ubuntu1                            Nautilus extension to share folder using Samba
ii  python-smbc                           1.0.10-0ubuntu1                            Python bindings for Samba clients (libsmbclient)
ii  samba                                 2:3.5.8~dfsg-1ubuntu2.3                    SMB/CIFS file, print, and login server for Unix
ii  samba-common                          2:3.5.8~dfsg-1ubuntu2.3                    common files used by both the Samba server and client
ii  samba-common-bin                      2:3.5.8~dfsg-1ubuntu2.3                    common files used by both the Samba server and client
ii  samba-tools                           2:3.5.8~dfsg-1ubuntu2.3                    Samba testing utilities
ii  smbclient                             2:3.5.8~dfsg-1ubuntu2.3                    command-line SMB/CIFS clients for Unix
ii  smbfs                                 2:4.5-2                                    Common Internet File System utilities - compatibility package
ii  winbind                               2:3.5.8~dfsg-1ubuntu2.3                    Samba nameservice integration server
andrew@andrew-Latitude-D520:~$

---

### Post by Wayne_V on 2011-08-30
that is still not the correct command:  

andrew@andrew-Latitude-D520:~$ smbclient -landisk -Uanonymous

you need:


andrew@andrew-Latitude-D520:~$ smbclient -[COLOR="Red"]L[/COLOR]landisk -Uanonymous

---

### Post by Morbius1 on 2011-08-30
> and then "$ sudo mount -t cifs //landdisk/disk -o user=anonymous /tmpmnt"
                                                      [QUOTE][sudo] password for andrew: 
mount: wrong fs type, bad option, bad superblock on //landisk/disk,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/QUOTE]You are missing a package:
```
sudo apt-get install cifs-utils
```If you are running an older version of Ubuntu it's:
```
sudo apt-get install smbfs
```> andrew@[COLOR=Blue]andrew-Latitude-D520[/COLOR]You said that this used to work from that machine? Your machine name is 5 characters too long so I'd correct it by editing smb.conf directly:
Add the following line to the [global] section of /etc/samba/smb.conf - right under the "workgroup" line:
```
netbios name = andrew-D520
```[COLOR=Blue]*It doesn't have to have that exact name but it has to be 15 characters or less in length.*[/COLOR]

If you also have samba server installed then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```You might want to run and post the output of the following command:
```
smbtree
```

---

### Post by winjeel on 2011-08-30
Thanks for your help.

> **Morbius1 said:**
> 

If you also have samba server installed then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```You might want to run and post the output of the following command:
```
smbtree
```

Four problems:
1. It seems nothing was installed
2. I'm not sure how to change the computer name (it has always been that name for more than two years, and the landisk worked fine)
3. No output for the  smbtree, but it did ask for a password
4. Still no access to the landisk

> andrew@andrew-Latitude-D520:~$ sudo apt-get install cifs-utils
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cifs-utils is already the newest version.
cifs-utils set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@andrew-Latitude-D520:~$ sudo service smbd restart
smbd start/running, process 6335
andrew@andrew-Latitude-D520:~$ sudo service nmbd restart
nmbd start/running, process 6348
andrew@andrew-Latitude-D520:~$ smbtree
Enter andrew's password: 
andrew@andrew-Latitude-D520:~$ smbtree
Enter andrew's password: 
andrew@andrew-Latitude-D520:~$ 

---

### Post by Morbius1 on 2011-08-30
[1] I would disable your firewall if you have done anything to it and then run smbtree again. If you havent done anything to the firewall then leave it alone. 
 
[2] Can you access the share directly by ip address. For example:
```
nautilus smb://192.168.0.100/disk
```

---

### Post by winjeel on 2011-08-30
> **Morbius1 said:**
> [1] I would disable your firewall if you have done anything to it and then run smbtree again. If you havent done anything to the firewall then leave it alone. 
 
[2] Can you access the share directly by ip address. For example:
```
nautilus smb://192.168.0.100/disk
```

[1] I did install a firewall, and then later uninstalled it, thinking it might be blocking my access to the landisk. Now, it is not installed, and
[2] Still no access from entering that smb address into terminal, my usual bookmark in the folder menu, or via firefox (in the past I've used firefox to access the admin functions of the drive).

---

### Post by Morbius1 on 2011-08-30
> [1] I did install a firewall, and then later uninstalled it, thinking it  might be blocking my access to the landisk. Now, it is not installed,  andFirestarter by any chance?

A simple remove is not enough. It must be purged:
```
 sudo apt-get purge firestarter
```In true Windows-like fashion you may be forced to install it and then purge it:
> **bodhi.zazen said:**
> This ^^

simply removing firstarter does not remove the configuration files.
```
sudo apt-get install firestarter 
sudo apt-get purge firestarter
```This is a long standing "bug" in  firestarter (conflicts with UFW, leaves config files when removed). As  firestarter is no longer maintained (it just keeps getting re-packaged),  I doubt this will ever be "fixed".

---

### Post by winjeel on 2011-08-30
Not firestarter, it was Firewall Configuration.

I just tried
```
sudo apt-get purge Firewall Configuration
```

But it said it could not locate the package

---

### Post by Morbius1 on 2011-08-30
Here's the problem I've got with this post. smbtree should show you all the machines on your network and their shares including the shares on the box you're running it from. You have samba running since you did a "smbd restart" and it shows it's running. You may not have created any shares on it but it should still show your own box but you can't even see yourself. smbtree desn't even give you any error messages.

Let's put this firewall issue to bed once and for all and I promise I won't bring it up again:

Install nmap:
```
sudo apt-get install nmap
```And run the following command:
```
sudo nmap -sS -sU -T4 192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of your own box.*[/COLOR]

What you should get for samba to work is something like this:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
If those ports aren't open then disable ufw:
```
sudo ufw disable
```And then run the nmap command again.

---

### Post by winjeel on 2011-09-04
Nope, didn't work. It seems to be getting ever more mysterious, as other than changing to the classic menu layout and installing then removing the firewall, nothing else had been changed on my computer, not even updates (until after I couldn't access my LAN drive).

In a moment I'll restart my computer to see if that I can try those commands again, so I posted this while I still had it.

> andrew@andrew-Latitude-D520:~$ sudo apt-get install nmap
[sudo] password for andrew: 
Sorry, try again.
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,777 kB of archives.
After this operation, 7,217 kB of additional disk space will be used.
Get:1 [http://jp.archive.ubuntu.com/ubuntu/](http://jp.archive.ubuntu.com/ubuntu/) natty/main nmap i386 5.21-1 [1,777 kB]
Fetched 1,777 kB in 3s (545 kB/s) 
Selecting previously deselected package nmap.
(Reading database ... 164160 files and directories currently installed.)
Unpacking nmap (from .../archives/nmap_5.21-1_i386.deb) ...
Processing triggers for man-db ...
Setting up nmap (5.21-1) ...
andrew@andrew-Latitude-D520:~$ sudo nmap -sS -sU -T4 192.168.0.100

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-09-05 10:53 JST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.08 seconds
andrew@andrew-Latitude-D520:~$ sudo ufw disable
Firewall stopped and disabled on system startup
andrew@andrew-Latitude-D520:~$ sudo nmap -sS -sU -T4 192.168.0.100

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2011-09-05 10:55 JST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.08 seconds


---

### Post by winjeel on 2011-09-04
Surprisingly, I could access the LAN drive before start up, and can access now. I'm running an AVG scan (anti-virus program) from a separate machine checking the LAN drive in case there was some non-Ubuntu related access problem, but how can I be sure that my Ubuntu wasn't infected? Could it really have been a problem with Ubuntu itself?

Thanks for your help. It's greatly appreciated.

---

