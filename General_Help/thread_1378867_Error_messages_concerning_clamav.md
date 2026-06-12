---
title: "Error messages concerning clamav"
date: 2010-01-11
forum: General Help
---

### Post by techiewannabe on 2010-01-11
I am running Jaunty and get the following messages when I try to Add/Remove any software:  

E: clamav-base: subprocess post-installation script returned error exit status 1 E: clamav-freshclam: dependency problems - leaving unconfigured 
 E: clamav: dependency problems - leaving unconfigured  
 E: clamav-daemon: dependency problems - leaving unconfigured  
 E: clamtk: dependency problems - leaving unconfigured 



Can someone help me with this?


Thanks.

---

### Post by dcstar on 2010-01-12
> **techiewannabe said:**
> I am running Jaunty and get the following messages when I try to Add/Remove any software:  

```
E: clamav-base: subprocess post-installation script returned error exit status 1 
 E: clamav-freshclam: dependency problems - leaving unconfigured 
 E: clamav: dependency problems - leaving unconfigured  
 E: clamav-daemon: dependency problems - leaving unconfigured  
 E: clamtk: dependency problems - leaving unconfigured 
```

Can someone help me with this?

Thanks.

Firstly, stop creating new threads that are exactly the same as one a few days ago.

This should tell you what the problem is.
```
apt-get install clamav-base
```

If you have added non-standard repositories or packages to your system, then you may find that you cannot install some standard packages any more.

---

### Post by techiewannabe on 2010-01-15
David:
Thanks for your note. When I gave the command you suggested, I received the following text.

tom@Compaq:~$ sudo apt-get install clam-base
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package clam-base
tom@Compaq:~$ 


Ideas, anyone?

Thanks.

Tom

---

### Post by john newbuntu on 2010-01-15
Please copy dcstar's command properly.  It is clamav-base.

---

### Post by techiewannabe on 2010-01-16
John:
Thanks for your post. After inputting the correct command, I got the following:[INDENT]tom@Compaq:~$ sudo apt-get install clamav-base
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav-base is already the newest version.
clamav-base set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.04) ...
id: clamav: No such user
chown: invalid user: `clamav:clamav'
chown: invalid user: `clamav:clamav'
install: invalid user `clamav'
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.95.3+dfsg-1ubuntu0.09.04); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-base (= 0.95.3+dfsg-1ubuntu0.09.04); however:
  Package clamav-base is not configured yet.
 clamav-daemon depends on clamNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              av-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamtk:
 clamtk depends on clamav (>= 0.90); however:
  Package clamav is not configured yet.
 clamtk depends on clamav-freshclam (>= 0.90) | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 clamav-daemon
 clamtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/INDENT]I'm afraid that I am still a newbie. I can see that the text tells me that certain things have not yet been configured or installed. However, I'm not sure how to correct that. I have tried to uninstall and reinstall the program, but still no luck.

Any suggestions would be appreciated.

Thanks.

Tom

---

### Post by john newbuntu on 2010-01-16
Open synaptic: system->administration->synaptic.  Search for "clam".
Mark the following packages: clamtk, clamav-freshclam, clamav, clamav-base, libclamav6.
Then click on apply.

---

### Post by techiewannabe on 2010-01-16
John:

Thanks for your suggestion. Each of the files that you mentioned were already installed, so I reinstalled them. Unfortunately, after the reinstall I got the same error messages as those listed above. 

I appreciate your willingness to help figure this thing out.

Tom

---

### Post by john newbuntu on 2010-01-16
Here is a forum which probably has a solution to your problem:

[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

---

### Post by techiewannabe on 2010-01-17
John:
Thanks for your suggestion. I visited the site and tried using the "-f" command without success. However, I need to try a couple of other ideas offered in that forum. I'll let you know if I'm successful.
Again, thanks for your help.
Tom

---

### Post by techiewannabe on 2010-01-18
John:

Thanks for your help. 

I am getting close to solving this problem. Now the number of error messages is down to only one. 
When I used the -f command I was able to install 3 out of the 4 problems. However, I'm still struggling with one of them. The terminal reports the following: 

tom@Compaq:~$ sudo apt-get -f install clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav-daemon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up clamav-daemon (0.95.3+dfsg-1ubuntu0.09.04) ...
chown: invalid user: `clamav:adm'
dpkg: error processing clamav-daemon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

If you, or anyone else, has any ideas on this, I would appreciate your help. (Again, I am very much a Linux newbie.)

Thanks, again.

Tom

---

### Post by john newbuntu on 2010-01-19
Here is a brute force method: 
In a terminal type gksudo nautilus.  Go to the directory /var/lib/dpkg/info/.  Copy all files that start with "clam" or "libclam" to another directory (say to a sub-folder in your home directory).  Then delete the copied files from /var/lib/dpkg/info.

Then open up a terminal and run 
```
sudo apt-get update
```
twice.

---

### Post by techiewannabe on 2010-01-23
John:

Thanks for your suggestion. 

When I followed your directions, the "gksudo nautilus" command took me to the Nautilus GUI. When I put in a search for "var/lib/dpkg/info/" I got zero items. However, when I search for "clamav," I get plenty of items (as you'd expect). However, I noticed that many of the files have similar names. For example, there are 10 files named "clamav," 2 named, "clamav base," and several others with similar names. 

All of these problems began when I reinstalled Jaunty and loaded up my backup files. I am wondering if I copied some files twice and that is the source of the problem.

Any ideas?

Thanks again for your help.

Tom

---

### Post by dcstar on 2010-01-24
> **techiewannabe said:**
> John:

Thanks for your suggestion. 

When I followed your directions, the "gksudo nautilus" command took me to the Nautilus GUI. When I put in a search for "var/lib/dpkg/info/" I got zero items. However, when I search for "clamav," I get plenty of items (as you'd expect). However, I noticed that many of the files have similar names. For example, there are 10 files named "clamav," 2 named, "clamav base," and several others with similar names. 

**All of these problems began when I reinstalled Jaunty and loaded up my backup files. I am wondering if I copied some files twice and that is the source of the problem.**


Thanks for the relevant information a week after you post the problem and we waste our time trying to fix it.

Totally remove all the clam packages in Synaptic (including configuration), empty the package cache in Synaptic and you might be able to install it again, but given that error message about the Clamav user possibly not.

---

### Post by techiewannabe on 2010-01-24
David:

Thanks for your note.

My apologies for the idiocy of my late report on the development of the problems I had with Clamav. When I first had the problem, the first thing that I did was to unintsall and reinstall Clamav. I assumed that it was an effective uninstall. (Apparently, that was my first mistake!) It didn't become obvious to me that I was wrong until I saw all of the Clamav duplicates that I mentioned in my last posting.

Nonetheless, apparently the problem is solved!

Thanks to you and John for your help with this.

I appreciate your patience with this newbie!

Tom

---

