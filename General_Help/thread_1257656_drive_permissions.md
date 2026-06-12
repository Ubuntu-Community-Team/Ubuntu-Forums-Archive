---
title: "drive permissions"
date: 2009-09-04
forum: General Help
---

### Post by rmausser on 2009-09-04
I have my hard drive partitioned so that all my documents are on a Fat32 partition (lets call this Documents) and my ubuntu and applications are on another.(call it Filesystem)

I do this so if I lose the system somehow, I can format the one partition while keeping my documents intact. 

But, I have two logins, one for my own personal stuff (login:rmausser), and another for work.(login:studio)

Right now my drive will read and write for my "rmausser" login, but the "studio" login will only read, not write. 

I need the drive to be able to have permissions for both logins all of the time. That is, if I switch users and keep both logged in, I want to still be able to read and write from the drive from ANY login.

I dont care about security...is this possible?

Please someone help, and for motivation, let me say that it is possible in Windows :).

Thanks

Rob

---

### Post by P4man on 2009-09-04
Have a look here:
[https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot](https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot)

You'll need to modify your fstab and apply permissions as you see fit. See the end of that segment.

If you'd rather do all that through a gui, then have a look at this program:
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

Its in the repositories, so you can install it with "sudo apt-get instal pysdm"

> **rmausser said:**
> 

Please someone help, and for motivation, let me say that it is possible in Windows :).


Im shocked. its possible in windows to have a less secure configuration ? :) BTW, in Windows can you restrict read or write rights on FAT32 to certain people or groups ?

Anyway Id advice you not to add such lines. Our motivation here is helping each other, not trying to prove linux is better than windows. You can be the judge of that, whether or not its better for *you*. But the "I can do this in windows, therefore it ought to be possible in linux" argument is kind tiresome, and frankly, wrong. If you want to be able to do everything windows can, run windows :)

---

### Post by rmausser on 2009-09-04
i know i was joking sorry.

I think that the permissions issues are one of the reasons that the average user doesnt use ubuntu more often. 

There should be a "remove permissions" setting so that I can just run everything as root all the time and never have to enter passwords. 

Some of us dont care about security. 

about 50% of the problems i have on linux are updates that break user privileges settings etc.

---

### Post by P4man on 2009-09-05
And I think that far more than 50% of the users that switch from windows to linux do so because they get rid of virusses, malware, spamware and other security threats breaking their windows. Throwing all file security out of the window would be a good start annihilating that advantage. Then you'd have the new users unintentionally breaking their linux because they start writing and changing stuff outside their /home without having a clue what /etc/sbin is, then blame linux for being fragile.

Not too mention the fact some of us like their setups secure :) Linux isnt windows, and doesn't want to mimic it. If you want a better windows than windows, Windows 7 is a good start :)

---

### Post by rmausser on 2009-09-06
i dont think that ubuntu or any linux distro should come with security features disabled, I just think that it should be easier to turn off if you wish. 

and recent versions of Windows have even harsher permissions and security restrictions now, so they are about the same. I think it is more how the kernel and OS is structured that allow for more malware and virus attacks within Windows.

Speaking of permissions, I still cannot get the external drive to read/write outside of one user. 


I edited the fstab using the Storage Device Manager program. 

I can change the UID to a specific user, but once I do that all other users are incapable of writing, just reading. 

If I do not use the fstab and manually mount the drive after login, I lose Samba permissions, and guests computers on my network cannot access files. 

We have a HTPC and I often use it to listen to my music downstairs while washing dishes, cooking etc. 

Is there any way that I can just say to linux "look, I don't give an F who uses this drive, just let everyone be able to use it, and read/write do whatever they want to it"

I dont want the drive to have an owner and all this other stuff, I just want it to get along with everything easily and nicely, mount automatically and be able to be written to by everyone.


Thanks

---

### Post by rmausser on 2009-09-15
Ok now this is just ridiculous. 

Whenever I send people files from this drive, or share them on the network, they are read-only. 

I set the permissions specifically to be public. What is going on? 

Is it because my drive is formatted for FAT32? Should I format it ext4? 

Will I have less problems with that? 

Please, let me know.

---

### Post by uylug on 2009-09-15
> **rmausser said:**
> Ok now this is just ridiculous. 

Whenever I send people files from this drive, or share them on the network, they are read-only. 

I set the permissions specifically to be public. What is going on? 

Is it because my drive is formatted for FAT32? Should I format it ext4? 

Will I have less problems with that? 

Please, let me know.

Fat32 is such an ancient filesystem with tons of problem so you should either format it to ntfs or ext4.

---

### Post by P4man on 2009-09-16
> **rmausser said:**
> Ok now this is just ridiculous. 

Whenever I send people files from this drive, or share them on the network, they are read-only. 


network shares are different from file permissions!
Its not because you have read/write/ownership rights on your home folder that everyone on the network (and therefore, internet) should have those rights. Install samba gui (in add/remove programs) and define shares and permissions of your network shares there.

Not sure what you mean by "sending" though.

---

