---
title: "Apt-Get is broken"
date: 2011-06-13
forum: General Help
---

### Post by pepsifx357 on 2011-06-13
Our power got cut off by the lightening storm the other day.  Well, today I go to install something and it doesn't work. 

I go to run apt-get update and I get this: 

```
apt-get: error while loading shared libraries: libapt-pkg-libc6.10-6.so.4.8: cannot open shared object file: No such file or directory

```

This error message along with a big fat error symbol in my notification area on my task bar that won't go away.  Anyone know how to fix this?

---

### Post by sikander3786 on 2011-06-13
Can you post the output of these commands please.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by el_koraco on 2011-06-13
First things first. 

```
sudo dpkg --configure -a

```

But that's unlikely to solve the problems. I googled your error report, and got this. 

[http://blog.opperschaap.net/2009/12/12/fixing-library-issues-on-ubuntu-lucid-10-04-development-release/]("http://blog.opperschaap.net/2009/12/12/fixing-library-issues-on-ubuntu-lucid-10-04-development-release/")

---

### Post by pepsifx357 on 2011-06-13
The first command didn't come back with anything.

```
ben@DAW:~$ sudo dpkg --configure -a
ben@DAW:~$ sudo apt-get install -f
apt-get: error while loading shared libraries: libapt-pkg-libc6.10-6.so.4.8: cannot open shared object file: No such file or directory

```

I googled my initial problem yesterday and found that the symlink had been broken somehow...I tried to fix it and I ended up deleting the file.  I tried to copy and paste the file in /usr/lib but that didn't work either.

---

### Post by el_koraco on 2011-06-13
I'm really shooting in the dark here, but how about you download apt from the link Temüjin gave you and try to install it with dpkg?

---

### Post by Yellow Pasque on 2011-06-13
I would download apt (the package containing the file in question) and install it with dpkg. [http://packages.ubuntu.com/lucid-updates/apt](http://packages.ubuntu.com/lucid-updates/apt)

EDIT: Use the link I gave instead of the one in the previous post (that's an older version of apt that came with the original Lucid).

---

### Post by pepsifx357 on 2011-06-13
She's all better!  All except for what looks like my funky repos that aren't working.  I'll fix that later.

```
ben@DAW:~/Downloads$ sudo dpkg -i apt_0.7.25.3ubuntu9.4_i386.deb 
[sudo] password for ben: 
(Reading database ... 190035 files and directories currently installed.)
Preparing to replace apt 0.7.25.3ubuntu9.4 (using apt_0.7.25.3ubuntu9.4_i386.deb) ...
Unpacking replacement apt ...
Setting up apt (0.7.25.3ubuntu9.4) ...

Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: file /lib/libresolv.so.2 is truncated

/sbin/ldconfig.real: file /lib/libresolv-2.11.1.so is truncated

/sbin/ldconfig.real: file /usr/lib/libresolv.so is truncated

ben@DAW:~/Downloads$ sudo apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Get:1 http://archive.canonical.com lucid Release.gpg [198B]          
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:2 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ lucid/main Translation-en_US
Get:3 http://ppa.launchpad.net lucid Release.gpg [316B]              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://archive.canonical.com lucid Release [8,215B]                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:5 http://security.ubuntu.com lucid-security Release [44.7kB]             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Get:6 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Get:7 http://ppa.launchpad.net lucid Release [14.0kB]                          
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:8 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]              
Get:9 http://archive.canonical.com lucid/partner Packages [13.4kB]             
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:10 http://security.ubuntu.com lucid-security/main Packages [194kB]         
Get:11 http://ppa.launchpad.net lucid/main Packages [3,873B]                   
Get:12 http://archive.canonical.com lucid/partner Sources [6,590B]             
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources 
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:13 http://us.archive.ubuntu.com lucid-updates/main Packages [502kB]
Get:14 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:15 http://security.ubuntu.com lucid-security/main Sources [58.2kB]        
Get:16 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:17 http://security.ubuntu.com lucid-security/universe Packages [71.5kB]  
Get:18 http://security.ubuntu.com lucid-security/universe Sources [21.3kB]     
Get:19 http://security.ubuntu.com lucid-security/multiverse Packages [4,555B]  
Get:20 http://security.ubuntu.com lucid-security/multiverse Sources [1,745B]   
Get:21 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B] 
Get:22 http://us.archive.ubuntu.com lucid-updates/main Sources [194kB]
Get:23 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:24 http://us.archive.ubuntu.com lucid-updates/universe Packages [203kB]
Get:25 http://us.archive.ubuntu.com lucid-updates/universe Sources [74.8kB]
Get:26 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]
Get:27 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,061B]
Fetched 1,481kB in 4s (340kB/s)   
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

Edit: Now that I'm looking at it.  Something is wrong still.  It fetched all of the files.  New problem?

---

### Post by Yellow Pasque on 2011-06-13
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386/comments/4](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/346386/comments/4)

Also, I would suggest marking libc6 for reinstall since libresolv.so seems to be corrupted.

---

### Post by pepsifx357 on 2011-06-13
I just deleted the file that was corrupted and now it's working fine.

Thanks for the help!

---

