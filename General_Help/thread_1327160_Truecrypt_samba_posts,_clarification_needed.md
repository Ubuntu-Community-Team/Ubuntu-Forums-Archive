---
title: "Truecrypt samba posts, clarification needed"
date: 2009-11-15
forum: General Help
---

### Post by Urob on 2009-11-15
I have done a 'truecrypt samba' search through forums, but have hard time to understand what i need to do.

_My situation: _

I have a truecrypt volume on a NAS.
The NAS (Iomega Home media drive) is only accessible via samba.
I can read/write to Nas, but can't mount a truecrypt volume: Permission denied.

I have found 2 solutions:

**Solution 1:**

1. Install fuse and sshfs
2. Add 'user_allow_other' to /etc/fuse.conf
3. Run sshfs

My Nas is on 192.168.0.100. Normally i access all files via network: smb://iomega-09c8e3/music ...
To access files on that network i do not need to enter a username or password.
I have made an empty folder called 'tc': /home/rob/Bureaublad/tc

Now comes the part i did not undertsand very well in forum post a week ago.
I thought i had to enter something like following:

rob@zwartje:~$ sudo sshfs rob@192.168.0.100:/ /home/rob/Bureaublad/tc -o allow_other
Executing this command returns:
read: Connection reset by peer 
????

**Solution 2:**

sudo mount -t smbfs \\\\192.168.0.100\\backups /home/rob/Bureaublad/tc -o username=rob

This seems to work. 
When clicking on folder 'tc' I can see the 4 subfolders: A, B, C and D
When i want to see the content of the subfolders, everything looks empty.
I suppose i need to add a parameter to be able to see the subfolders ?

???

Solution:   [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

