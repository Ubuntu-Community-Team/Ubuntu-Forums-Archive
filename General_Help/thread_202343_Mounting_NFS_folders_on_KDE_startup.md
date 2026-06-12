---
title: "Mounting NFS folders on KDE startup"
date: 2006-06-23
forum: General Help
---

### Post by Daiver on 2006-06-23
So, I have a huge problem with amaroK and my mp3s.  Basically aK rebuilds the database everytime it fires up and the mp3 folders are not mounted.  To make sure that this didn't happen again, I added this line into de .bashrc in my users home folder:

sudo mount -t nfs 192.168.10.2:/mnt/sdb1/Mp3 /media/mp3/new

The only problem with this is that it requires the root password to mount, making my solution completely useless.

How can I mount without needing root privileges or how can I add the password to that line?

Thanks!

---

### Post by feathers on 2006-06-23
You don't need the password if you add the following line to /etc/fstab: 
192.168.10.2:/mnt/sdb1/Mp3 /media/mp3/new nfs user,auto 0 0 

Then this directory is mounton startup. If you don't want this to happen at startup, use noauto instead of auto. User means that users can mount the directory. You might even try autofs for more convenience.

---

### Post by Daiver on 2006-06-23
Hi feathers, thank you for you quick reply.

The problem with mounting at startup is that I'm on a wireless network, so I need Dapper to first get the wireless network up and running and then mount.  That's why I chose the "on KDE startup" approach.

Also, what would happen if I take my laptop to another location and the PC where the mp3s are stored is not found?  Will it hang my system?

---

### Post by yota on 2006-06-23
By adding a line like this in /etc/sudoers file (note that you should use the 'visudo' command to edit that file) you can enable mounts without a password:
```

*your_username* *your_hostname*=(root) NOPASSWD: /bin/mount

```

But a more elegant way is to enable autofs that handle all nfs mounts dynamically; see

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

hope this helps!

---

### Post by Daiver on 2006-06-23
Hi yota,

your_username and your_hostname referrs to the remote machine's user or to the local information?

---

### Post by yota on 2006-06-25
Hi Daiver, sorry for the delay, but I try to spend as little time as possible in front of the computer on the weekend :-)

*your_username* and *your_hostname* are both local:

From 'man sudo'
> 
DESCRIPTION
       sudo allows a permitted user to execute a command as the superuser or
       another user, as specified in the sudoers file.

So configuring sudoers you can grant a specified user (*your_username*) the right to execute a command or more as root (just /usr/bin/mount in this case) from a specified host (*your_hostname*) on the local machine and NOPASSWD specify that a password is not required.
The syntax of the sudoers file is quite complex, you can see everything with 'man sudoers' in a shell.

Note that once sudoers is configured you have to use 'sudo mount' instead of just  'mount' to have it work without password.

Have a look at [http://www.wlug.org.nz/SudoHowto](http://www.wlug.org.nz/SudoHowto) too.

Let me know if it worked.

---

### Post by Daiver on 2006-06-25
Hi yota,

It's a good policy, maybe I should try to adopt it.

What would happen if I'm away from home and it can't find the resources that it wants to mount?  Will it crash my laptop or make it slow while it tries to mount something that's not there?

---

### Post by feathers on 2006-06-26
[QUOTE=Daiver]Hi feathers, thank you for you quick reply.

The problem with mounting at startup is that I'm on a wireless network, so I need Dapper to first get the wireless network up and running and then mount.  That's why I chose the "on KDE startup" approach.[/QUOTE]
Well, this is not automatic but comfortable: Use kdiskfree to mount the directory. Use the noauto option in /etc/fstab so it doesn't try to mount the directory at startup. 

> Also, what would happen if I take my laptop to another location and the PC where the mp3s are stored is not found?  Will it hang my system?
It will try to mount the directory for a couple of minutes but nothing dangerous will happen.

---

### Post by yota on 2006-06-26
> 
What would happen if I'm away from home and it can't find the resources that it wants to mount? Will it crash my laptop or make it slow while it tries to mount something that's not there?

Agree with feathers, but If you move often you definitely want to go with autofs: it's really the best way to handle nfs shares on demand.
Autofs creates a /net folder and a when someone (you or a program) do a 'cd /net/*servername*/*sharename*' automatically mounts the *sharename* share from *servername* machine on that dir; if it's not available it fails immediatly.

Once tried one time you'll never go back! ;-)

---

### Post by Daiver on 2006-06-26
Alright, I'm going with the autofs approach then.

I already got autofs via apt-get and now I'm looking at /etc/auto.master but have no clue on what I should edit there.  Do you think you can walk me through? 

I went to / but I didn't see a net folder in there.

Oh, and thanks for the amazing help so far =)

---

### Post by yota on 2006-06-27
You simply have to uncomment the line of /net so it looks like this (I don't know why autofs is shipped with everything disabled):
```

/net    /etc/auto.net

```
and then do a
```

sudo /etc/init.d/autofs restart

```

And your're done!

---

### Post by Daiver on 2006-06-27
Alright.  I did that and now I see the net folder in /.  However, I don't see anything inside that folder.  How do I access the files?

---

### Post by Daiver on 2006-06-27
Uhm, it also created something called usplash_fifo in /.  What's this?

---

### Post by AndyCooll on 2006-06-27
[QUOTE=Daiver]The problem with mounting at startup is that I'm on a wireless network, so I need Dapper to first get the wireless network up and running and then mount.  That's why I chose the "on KDE startup" approach.

Also, what would happen if I take my laptop to another location and the PC where the mp3s are stored is not found?  Will it hang my system?[/QUOTE]

I realise I'm replying a couple of days after this thread begun and I have to admit that I'm not fully up to speed with wireless etc. However, I have to ask, why does being on "wireless network" make a difference to the usual boot procedure? My laptop uses my wireless network and has directories which automount because of entries in fstab (my home directory for instance!) without any problems.

And all that happens if the "mounts" can't be found on boot-up is that the link isn't made (and hence is unavailable). The system gives up after a short time and continues to boot as if they're not there.

:cool:

---

### Post by Daiver on 2006-06-27
Well, I assume that for it to mount remote shares it needs to have a wireless link up and running.  For some reason, I was also assuming that the system mounted whatever it found before it got to the network interfaces.

Is this completely off track?

---

### Post by yota on 2006-06-27
> 
Alright. I did that and now I see the net folder in /. However, I don't see anything inside that folder. How do I access the files?


just try to enter (with cd, nautilus or anything else) /net/*ip_address_of_machine_with_nfs_shares*/ ,it will be dynamically created the first time you access it, so it's perfectly normal that you don't see anything in /net now.
To confirm that autofs is working correctly you shuld see something like this with 'mount':
```

yota@linbook:~$ mount
...
automount(pid4551) on /net type autofs (rw,fd=4,pgrp=4551,minproto=2,maxproto=4)
...

```

Keep on trying, we're almost there!

---

### Post by Daiver on 2006-06-27
Hi yota,

Yep.  *Almost* there. ;)

So I went into /net with Konqueror and it's empy.  I typed in "/net/192.168.10.2/" with and without the trailing backslash and it gave me this: *bash: cd: /net/192.168.10.2: No such file or directory*.

Here's my outcome of *mount*:

[I]daiver@ulysses:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda7 on /media/sda7 type vfat (rw,utf8,umask=007,gid=46)
automount(pid4403) on /net type autofs (rw,fd=4,pgrp=4403,minproto=2,maxproto=4)[/I]

So, it's there, but I can't see it just yet :P

Any ideas?

---

### Post by yota on 2006-06-27
Mhh... how is the share exported on the other side?
Please post your /etc/exports of the machine hosting the share.

It should be something like this:
```

/share          192.168.10.1/255.255.255.0(rw,sync,nohide,all_squash,anonuid=1000,anongid=1000)

```

Adjust the netmask to suite your network settings and set anonuid, anongid to match uid and gid of a user on the machine exporting the folder who has appropriate rights on the folder exported.

You can try to cd to /net/*ip_address*/*sharename*/ too, and see if it works better.

---

### Post by Daiver on 2006-06-27
Here's what I have on the host:
[I]
[keyser@localhost etc]$ cat exports
# generated by drakhosts.pl
/mnt/sdb1/Mp3 192.168.10.3(all_squash,anonuid=65534,anongid=65534,sync,secure,ro)
/mnt/sdb1/mp3locked 192.168.10.3(all_squash,anonuid=65534,anongid=65534,sync,secure,ro)
[/I]

For future reference, it's running PCLinuxOS 0.92.  Is this information correct? I notice that instead of /share it says /mnt.  Should I change something?

Thank you again for the amazing help.

---

### Post by yota on 2006-06-28
> 
Thank you again for the amazing help.


You're welcome :-)

Nfs configuration seems ok, but allows connections only from 192.168.10.3 and from "secure" clients, if you have DHCP this can be a problem, we can try to relax some restrictions and see how it goes...
comment out this line:
```

/mnt/sdb1/Mp3 192.168.10.3(all_squash,anonuid=65534,anongid=65534,sync,secure,ro)

```
and replace it with:
```

/mnt/sdb1/Mp3 (all_squash,anonuid=65534,anongid=65534,sync,insecure,ro)

```

now restart nfs server daemon, then try to cd /net/192.168.10.2/mnt/sdb1/Mp3/ from client machine and let me know.
If it works you can restore the more secured settings one by one to spot which is giving problems.

If it still doesn't work, have a look at /var/log/syslog (both at server an at client) just after the failed cd attempt; maybe there can be infos about what's going on.

---

### Post by Daiver on 2006-06-28
Alright, I did the changes you requested and still no luck.  I get the same No such file or directory.

However, check out the logs:

Client:

[I]Jun 28 05:00:49 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun 28 05:00:49 localhost anacron[4689]: Job `cron.daily' terminated
Jun 28 05:00:49 localhost anacron[4689]: Normal exit (1 job run)
Jun 28 05:01:01 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Jun 28 05:01:20 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Jun 28 05:01:24 localhost dhclient: No DHCPOFFERS received.
Jun 28 05:01:24 localhost dhclient: No working leases in persistent database - sleeping.
Jun 28 05:05:03 localhost automount[5920]: >> /etc/auto.net: line 40: --no-headers: command not found
Jun 28 05:05:03 localhost automount[5920]: lookup(program): lookup for 192.168.10.2 failed
Jun 28 05:05:03 localhost automount[5920]: failed to mount /net/192.168.10.2[/I]


Host:

[I]Jun 28 05:05:58 localhost nfs: nfsd shutdown succeeded
Jun 28 05:05:58 localhost nfs: Shutting down NFS services:  succeeded
Jun 28 05:05:58 localhost exportfs[8543]: No host name given with /mnt/sdb1/Mp3 (all_squash,anonuid=65534,anongid=65534,sync,insecure,ro), suggest *(all_squash,anonuid=65534,anongid=65534,sync,insecure,ro) to avoid warning
Jun 28 05:05:58 localhost exportfs: exportfs: No host name given with /mnt/sdb1/Mp3 (all_squash,anonuid=65534,anongid=65534,sync,insecure,ro), suggest *(all_squash,anonuid=65534,anongid=65534,sync,insecure,ro) to avoid warning
Jun 28 05:05:58 localhost nfs: Starting NFS services:  succeeded
Jun 28 05:05:58 localhost nfs: rpc.nfsd startup succeeded
Jun 28 05:05:59 localhost mountd[8569]: No host name given with /mnt/sdb1/Mp3 (ro,sync,wdelay,hide,nocrossmnt,insecure,root_squash,all_squash,subtree_check,secure_locks,acl,mapping=identity,anonuid=65534,anongid=65534), suggest *(ro,sync,wdelay,hide,nocrossmnt,insecure,root_squash,all_squash,subtree_check,secure_locks,acl,mapping=identity,anonuid=65534,anongid=65534) to avoid warning
Jun 28 05:05:59 localhost nfs: rpc.mountd startup succeeded[/I]

Please note that DHCP is off in my router, so client is always 192.168.10.3 and host is always 192.168.10.2.

---

### Post by yota on 2006-06-28
> 
Jun 28 05:05:03 localhost automount[5920]: >> /etc/auto.net: line 40: --no-headers: command not found

Weird... but it seems that we have problems with the showmount command (that's used to get the share list).
Try this two commands from a shell:
```

/sbin/showmount --no-headers -e 192.168.10.2

```
and
```

showmount -e 192.168.10.2 | tail +2

```

if one works and lists correctly the shares on 192.168.10.2 we can fix /etc/auto.net

> 
Jun 28 05:05:58 localhost exportfs: exportfs: No host name given with /mnt/sdb1/Mp3 (all_squash,anonuid=65534,anongid=65534,sync,insecure,ro), suggest *(all_squash,anonuid=65534,anongid=65534,sync,insecure,ro) to avoid warning


You can accept the suggestion to suppress the warning message by adding the '*' (my fault!)

---

### Post by Daiver on 2006-06-28
Hi yota,

It appears as if showmount doesn't exist in my computer.
[I]
daiver@ulysses:~$ /sbin/showmount --no-headers -e 192.168.10.2
bash: /sbin/showmount: No such file or directory

daiver@ulysses:/sbin$ showmount -e 192.168.10.2 | tail +2
bash: showmount: command not found[/I]

I'm sorry that this is taking so long, I could have sworn that it would be simpler.  If you ever come down to Uruguay, I'll buy you a beer. :mrgreen:

Also, please note that the warning message is still there.  Here's how the line looks after editing:

/mnt/sdb1/Mp3 *(all_squash,anonuid=65534,anongid=65534,sync,insecure,ro)

---

### Post by yota on 2006-06-28
> 
yota@linbook:/etc$ dpkg -S /sbin/showmount
nfs-common: /sbin/showmount

So /sbin/showmount is in nfs-common: go and apt-get it! (eventually with --reinstall) 

> 
I'm sorry that this is taking so long, I could have sworn that it would be simpler. If you ever come down to Uruguay, I'll buy you a beer.


Well... i thought it should have been simpler too; moreover autofs depends on nfs-common, so I don't know why it has not been automatically installed on your machine. :-k 
Anyway no worries!  

> 
Also, please note that the warning message is still there. Here's how the line looks after editing:

/mnt/sdb1/Mp3 *(all_squash,anonuid=65534,anongid=65534,sync,inse cure,ro)

Have you restarted nfs server daemon after editing?

---

### Post by yota on 2006-06-28
I have seen that autofs "recommends" nfs-common, but don't actually depends on it... Maybe we have got the point, let me know.

---

### Post by Daiver on 2006-06-28
Yota, make that two beers.  

PROBLEM SOLVED!  

Now I can cd into /net/192.16.10.2 and you were right, it IS amazing.  Not only does it work like a charm, but it also mounts everything extremely fast.  It's like if those mounts were local!

Thank you very, very, very much!

=)

---

