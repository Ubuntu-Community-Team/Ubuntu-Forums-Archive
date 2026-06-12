---
title: "Too many permissions for FTP users"
date: 2009-08-30
forum: General Help
---

### Post by Kyroswolf on 2009-08-30
I'm setting up an old desktop as a file server.  I have the much of it setup.  I want to allow ftp connections so that an off site user (in this case my mother) can upload her ever expanding library of photos to the server and free up space on her meager and aging desktop.

To this end I have ubuntu server 9.04 installed.   I installed vsftpd also.  Local users are enabled.  I have changed the home directory for the local/ftp users so that all uploaded files will go to a seperate HD (mounted on media/store/) from the OS HD. 

For example:  User test has a home directory of /media/store/test/.  I can ftp to the server as test.  The problems is he can see the file structure above his home directory.  I want users to only see their home directory, nothing above it.  How can I fix this?

> Ok, so this turned out to be easier than I thought.  in /etc/vsftpd.conf there is a line that is commented out.

chroot_local_user=YES

Uncomment this line and now ftp users will see there home directory as root.

Chalk this one up to Resolved.

---

### Post by Kyroswolf on 2009-08-31
Ok through my own research I know this is a chmod issue.  The users need 777 to their home directory but not to the parent directorys.  after ls -ld on each directory users have full rights to their home directory and /media/store/ and read and execute rights to / and /media.

I need the correct chmod XXX to remove the read/execute for /, /media/, and /media/store/.  Any help on this.  My own efforts are failing.

---

### Post by Kyroswolf on 2009-09-01
Ok, so this turned out to be easier than I thought.  in /etc/vsftpd.conf there is a line that is commented out.

chroot_local_user=YES

Uncomment this line and now ftp users will see there home directory as root.

Chalk this one up to Resolved.

---

