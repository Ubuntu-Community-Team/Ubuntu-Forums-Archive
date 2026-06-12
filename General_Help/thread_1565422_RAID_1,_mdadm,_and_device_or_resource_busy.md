---
title: "RAID 1, mdadm, and device or resource busy"
date: 2010-08-31
forum: General Help
---

### Post by SkittlesAreYum on 2010-08-31
Hi all,

I'm a major Ubuntu and Linux newbie, so of course I'm trying to set up my own software RAID.  :)  Things aren't going well, which I'll get to in a minute.  In the meantime, some background:

I have installed Ubuntu 10.4 desktop.  All went fine during the installation.  I only partitioned the HDD I was installing the OS to; I have two other HDDs that I want to RAID (level 1) together (1.5 TB each, identical models).  

So, I added a partition table to the HDDs and partitioned them both as one partition with ext4.  So far so good.  I then attempted to create a RAID array using the following command:

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

I don't remember if I had to run the assemble command, but if I should have then assume I did.  Regardless, everything seemed to work: the command(s) did not return an error and the RAID array appeared in the Computer place (I forgot the exact name, but something like 1.5TB RAID 1).  I was able to open it in the UI without an error, although I did not test copying files.

Then I had to turn off the computer and come back later.  When it booted the RAID array was no longer in the Computer place.  I did "ls" on /dev and there is no "md0".  OK, so I tried assembling it again and creating it:

 ```

mark@mark-server:~$ sudo mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted
mark@mark-server:~$ sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Mon Aug 30 21:57:55 2010
mdadm: create aborted

```


Not good.  Also, when I open gparted from the terminal, I notice the follow message


```

mark@mark-server:~$ sudo gparted
[sudo] password for mark: 
======================
libparted : 2.2
======================
Could not stat device /dev/md0 - No such file or directory.

```


I cannot even format /dev/sdb1 in gparted.  What's strange is I rebooted my system many times before creating the RAID, and I was always able to format /dev/sdb1.  Now that I try creating a RAID that apparently does not exist anymore, it's busy all the time?

I've searched the web and found many people with this "device or resource busy" error.  No one seemed to have a solution.  Some people mentioned the SATA controller might be an issue, but have no idea how to check that.  I have a Foxconn A7VML/A76ML series motherboard.  I don't know of any more logs to check or commands to run.  Any Ubuntu/Linux/mdadm gurus have any ideas?

Thanks in advance!

---

### Post by SkittlesAreYum on 2010-09-01
Also, feel free to move this message to the appropriate forum if I located it incorrectly.  I thought about putting it in the server help forum because I do plan on using it as a server, but I have desktop Ubuntu installed (due to server Ubuntu being unable to install on a USB key; it still thinks a CD drive should be present).

---

### Post by SkittlesAreYum on 2010-09-02
No one has any ideas? :(

---

### Post by hayhursm on 2010-09-02
> **SkittlesAreYum said:**
> No one has any ideas? :(
 
From one noob speaking to another...would this possibly be a **"mount"** issue?  Go to **"System" "Administration" "Disk Utility"** and see if it is there and mountable.  I hope I'm not leading you astray because I haven't begun to dig into **mdadm** yet.

---

### Post by Azdour on 2010-09-02
I've recently installed mdadm and seem to be doing something similar to you.

I created the RAID drive with:
```

sudo mdadm --create --verbose --auto=yes /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```
I then did:
```

watch cat /proc/mdstat

```
And waited until the drives had synced.

On my Ubuntu 10.04 the mdadm.conf file was created incorrectly. I ran:
```

sudo mdadm --examine --scan --config=mdadm.conf

```

Copied the ARRAY line, then edited the /etc/mdadm/mdadm.conf file. Mine had an ARRAY line but the uuid of the drive was different. If it has an ARRAY line just overwrite it, but sometimes I have seen that there is no ARRAY so I would place it under the DEVICES line.

After that I rebooted it all seemed to work. Not sure if this will help or not with your problem.

---

### Post by hayhursm on 2010-09-02
> **Azdour said:**
> I've recently installed mdadm and seem to be doing something similar to you.
 
I created the RAID drive with:
```

sudo mdadm --create --verbose --auto=yes /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```
I then did:
```

watch cat /proc/mdstat

```
And waited until the drives had synced.
 
On my Ubuntu 10.04 the mdadm.conf file was created incorrectly. I ran:
```

sudo mdadm --examine --scan --config=mdadm.conf

```
 
Copied the ARRAY line, then edited the /etc/mdadm/mdadm.conf file. Mine had an ARRAY line but the uuid of the drive was different. If it has an ARRAY line just overwrite it, but sometimes I have seen that there is no ARRAY so I would place it under the DEVICES line.
 
After that I rebooted it all seemed to work. Not sure if this will help or not with your problem.
 
[COLOR=black][FONT=Verdana]I hope I'm not getting off subject here but are you impressed with the SoftwareRAID?  Let's say I have two HDD's in a RAID 1 and a third HDD strictly for the OS and other Apps.  If I built the RAID 1 setup using mdadm on the two HDD's and decided to format or do a fresh install of Ubuntu on the third HDD, would I lose all my data on the two RAID 1 drives?  Basically, will it still work if I install a different OS’?  I was just wondering since the SoftwareRAID is obviously dependant on software and not hardware.[/FONT][/COLOR]

---

### Post by Azdour on 2010-09-03
Hi,

I've only just started to play with Software RAID. I had a 500gb drive which I installed Ubuntu on, and 2x250gb drives in RAID 1 (this I mounted as /home).

I then swapped the 500gb for 160gb, reinstalled Ubuntu and then mdadm. I think it found the RAID 1 drive again and I could see my home directory (not mounted because I had yet to modify the fstab, I could mount it myself and see its contents). I guess this is something I need to test more to confirm but maybe someone else here may be able to clarify/confirm this.

I think it does write some info directly on the drive, because if you ever wanted to scrap the RAID one of the things you have to do is:
<code>
sudo mdadm --zero-superblock /dev/sda
</code>

The only disadvantage I have found so far with software RAID is that it can be a bit of effort to fully remove :)

---

### Post by hayhursm on 2010-09-07
> **Azdour said:**
> Hi,
 
I've only just started to play with Software RAID. I had a 500gb drive which I installed Ubuntu on, and 2x250gb drives in RAID 1 (this I mounted as /home).
 
I then swapped the 500gb for 160gb, reinstalled Ubuntu and then mdadm. I think it found the RAID 1 drive again and I could see my home directory (not mounted because I had yet to modify the fstab, I could mount it myself and see its contents). I guess this is something I need to test more to confirm but maybe someone else here may be able to clarify/confirm this.
 
I think it does write some info directly on the drive, because if you ever wanted to scrap the RAID one of the things you have to do is:
<code>
sudo mdadm --zero-superblock /dev/sda
</code>
 
The only disadvantage I have found so far with software RAID is that it can be a bit of effort to fully remove :)
 
Thanks for the info, if you discover anything new with your testing then please let me know.  :)

---

