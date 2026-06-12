---
title: "Write HFS+ in Ubuntu"
date: 2009-07-22
forum: General Help
---

### Post by crispygoat on 2009-07-22
I've read several threads regarding HFS+ and Ubuntu but it still won't work. I backed up an HFS+ external hard drive on a Ubuntu platform. Afterwards, I formated the hard drive to Mac OS Extended (Non-Journaled). I set the permissions (from the Mac) so that everyone can Read/Write the hard drive but it still says I do not have permission to write on the drive :confused:.

I'm also wondering if I'll be able to modify the files I created on the hard drive with the Mac in Ubuntu and vice-versa.

Thank you.

---

### Post by synapsys on 2009-07-22
> **crispygoat said:**
> I set the permissions (from the Mac)

Good. Now you need to set the permissions (from Ubuntu) to allow you to write to the drive. The easiest way to do this is to change the permissions of the mount point of the drive while the drive is un-mounted. If you want to make this permanent you'll need to edit your fstab.

Ubuntu follows it's own permissions set by the drives mount point.

---

### Post by crispygoat on 2009-07-22
Whenever I go to the Permissions tab in Properties I get a message saying "The permissions of "x" could not be determined. How do I change permissions at mount point and edit the fstab?

thanks

---

### Post by crispygoat on 2009-07-23
bump

I've read about Fstab. The problem is that the drive already mounts by itself. I just need to set permission to "write". When I copied the line from mtab to fstab, the drive wouldn't mount by itself and I did not have permission to mount the volume.

thanks

---

### Post by synapsys on 2009-07-23
The easiest thing to do would be browse to you /media folder. This folder contains all your currently mounted external hard drives. The hfs drive should be mounted in a folder called 'disk' or something like that. If you are not allowed to access this folder as a normal user you may need to access it as root. In this case open up a terminal Applications >> Accessories >> Terminal and type:

```
sudo nautilus /media/nameofyourfolder
```

This will temporarily give you full access to the drive. If you need to make this permanent you will need to edit a text file located in the /etc folder called fstab (/etc/fstab) There are plenty of tutorials on this already. You can probably google it, or search these forums.

---

### Post by crispygoat on 2009-07-23
Even when root the volume is read only :confused:

---

### Post by synapsys on 2009-07-23
> **synapsys said:**
> browse to you /media folder..

---

### Post by crispygoat on 2009-07-23
Whether I browse to myname/media/externalhd or from root I get the same error message. I've attached a screen shot. I do get some kind of error.

---

### Post by synapsys on 2009-07-23
It appears you need to turn journaling off....

[http://ubuntuforums.org/showthread.php?t=98286](http://ubuntuforums.org/showthread.php?t=98286)

---

### Post by crispygoat on 2009-07-23
Journal has always been turned off :confused:.

I tried using chmod

```

chmod a=rwx /media/external
chmod: changing permissions of '/media/external': Read-only file system

```And like stated in the link you sent me, I also tried

```

sudo chown -R francis /media/external
[sudo] password for francis: 
chown: changing ownership of `/media/external/.fseventsd/0000000000024bfb': Read-only file system
chown: changing ownership of `/media/external/.fseventsd/fseventsd-uuid': Read-only file system
chown: changing ownership of `/media/external/.fseventsd': Read-only file system
chown: changing ownership of `/media/external/.HFS+ Private Directory Data\r': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/.store.db': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexArrays': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexCompactDirectory': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexDirectory': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexGroups': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexHead': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexIds': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexPositions': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexPostings': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.indexUpdates': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.shadowIndexGroups': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/0.shadowIndexHead': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/indexState': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/journalExclusion': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/journalLive': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/journalSync': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexArrays': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexCompactDirectory': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexDirectory': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexGroups': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexHead': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexIds': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexPositions': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexPositionTable': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexPostings': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexTermIds': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.indexUpdates': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexArrays': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexCompactDirectory': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexDirectory': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexGroups': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexHead': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexPositionTable': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/live.0.shadowIndexTermIds': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/store.db': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41/store.updates': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores/C6E77812-6E2A-42CA-8457-4404A8BA1B41': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/Stores': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1/VolumeConfig.plist': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100/Store-V1': Read-only file system
chown: changing ownership of `/media/external/.Spotlight-V100': Read-only file system
chown: changing ownership of `/media/external/.Trashes/501': Read-only file system
chown: changing ownership of `/media/external/.Trashes': Read-only file system
chown: changing ownership of `/media/external': Read-only file system

```Still no luck.

ps: thanks a lot for your help.




(On the Mac)

Information: Storage Room
Name: Storage Room
Type: Volume

Disk Identifier: disk1s1
Writable: Yes
Owners Enabled: No
Supports Journaling: Yes
Journaled: No

---

### Post by synapsys on 2009-07-24
Have you installed the package with hfs manipulation tools? I think it is called hfsprogs or hfsutils or something like that.

---

