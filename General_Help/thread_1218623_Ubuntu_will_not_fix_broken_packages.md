---
title: "Ubuntu will not fix broken packages"
date: 2009-07-20
forum: General Help
---

### Post by saleenman on 2009-07-20
Hi, I recently tried to install "Spashy" and the install failed. It said that I needed to fix broken packages. So I ran the "sudo apt-get -f install" command and I get this output:

```
austin@Bartz-PC0:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  splashy
Suggested packages:
  console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1180kB of archives.
After this operation, 1831kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 164860 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-3ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I have tried every thing that I could think of, but still no luck.

Thanks in advance,
Austin

---

### Post by michy99 on 2009-07-20
Have you tried```
sudo dpkg --configure -a
```

---

### Post by saleenman on 2009-07-20
Just did, and still no luck this is the output:

```
austin@Bartz-PC0:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of splashy-themes:
 splashy-themes depends on splashy (>= 0.3.12-1); however:
  Package splashy is not installed.
dpkg: error processing splashy-themes (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy-themes

```

---

### Post by utnubuuser on 2009-07-20
Try reinstalling splashy

---

### Post by saleenman on 2009-07-20
Tried that, and it wont let me because of the broken package.

---

### Post by michy99 on 2009-07-20
Another try:```
sudo rm /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
sudo apt-get update
```

---

### Post by saleenman on 2009-07-20
Still nothing, I just get the same output.

---

### Post by michy99 on 2009-07-20
What do you get for```
ls -la /var/lib/apt
```

---

### Post by saleenman on 2009-07-20
```
austin@Bartz-PC0:~$ ls -la /var/lib/apt
total 48
drwxr-xr-x  6 root root  4096 2009-07-18 09:56 .
drwxr-xr-x 57 root root  4096 2009-07-16 18:41 ..
-rw-r--r--  1 root root   209 2009-07-15 09:28 cdroms.list
-rw-r--r--  1 root root  8772 2009-07-18 09:56 extended_states
drwxr-xr-x  2 root root  4096 2009-04-20 09:00 keyrings
drwxr-xr-x  3 root root 12288 2009-07-20 21:03 lists
drwxr-xr-x  3 root root  4096 2009-04-20 08:59 mirrors
drwxr-xr-x  2 root root  4096 2009-07-15 19:10 periodic

```

---

### Post by michy99 on 2009-07-20
How about this```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.backup
sudo apt-get update
```

---

### Post by saleenman on 2009-07-20
I get this code and this error when I tried to install a package.
```
austin@Bartz-PC0:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.backup
[sudo] password for austin: 
austin@Bartz-PC0:~$ sudo apt-get update
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com jaunty Release.gpg                            
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US                 
Hit http://archive.canonical.com jaunty Release                                
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://ppa.launchpad.net jaunty Release                                    
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com jaunty-backports Release.gpg                  
Hit http://archive.canonical.com jaunty/partner Packages                       
Ign http://us.archive.ubuntu.com jaunty-backports/main Translation-en_US       
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://ppa.launchpad.net jaunty/main Packages                              
Ign http://us.archive.ubuntu.com jaunty-backports/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty-backports/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty-backports/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com jaunty-proposed Release.gpg                   
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Ign http://us.archive.ubuntu.com jaunty-proposed/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/main Translation-en_US        
Ign http://us.archive.ubuntu.com jaunty-proposed/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-proposed/universe Translation-en_US    
Hit http://us.archive.ubuntu.com jaunty Release                   
Hit http://us.archive.ubuntu.com jaunty-updates Release           
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com jaunty-backports Release                      
Hit http://us.archive.ubuntu.com jaunty-proposed Release                       
Hit http://us.archive.ubuntu.com jaunty/main Packages                          
Hit http://us.archive.ubuntu.com jaunty/restricted Packages       
Hit http://us.archive.ubuntu.com jaunty/main Sources              
Hit http://us.archive.ubuntu.com jaunty/restricted Sources        
Hit http://us.archive.ubuntu.com jaunty/universe Packages         
Hit http://us.archive.ubuntu.com jaunty/universe Sources          
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages       
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources        
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages     
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources      
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages 
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources  
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-backports/main Packages   
Hit http://us.archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-backports/universe Packages
Hit http://us.archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/main Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-proposed/universe Packages
Hit http://wine.budgetdedicated.com jaunty Release.gpg
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US
Hit http://wine.budgetdedicated.com jaunty Release
Ign http://wine.budgetdedicated.com jaunty/main Packages
Hit http://wine.budgetdedicated.com jaunty/main Packages
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.

```

"Software index is broken"

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

---

### Post by michy99 on 2009-07-20
Okay, I guess that wasn't a good idea```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

---

### Post by Seq on 2009-07-20
You've got two packages trying to own the same file. Deleting caches and reinstalling isn't going to fix that. You will have to divert one using dpkg-divert.

```
sudo dpkg-divert --package lsb-base --divert /etc/lsb-base-logging.sh.splashy --rename /etc/lsb-base-logging.sh
```

This will make a diversion in favour of lsb-base. splashy's copy will be installed as _/etc/lsb-base-logging.sh.splashy_ instead. This will keep lsb-base's version working properly. Splashy probably won't work though (it likely needs some changes to that script, which is why it is attempting to replace it).

If you want to use splashy's version, simply change the --package parameter to favour splashy (and maybe change the suffix on the diversion)

```
sudo dpkg-divert --package **splashy** --divert /etc/lsb-base-logging.sh.**lsb-base** --rename /etc/lsb-base-logging.sh
```

If you do this, you will have to remember to remove the diversion after you remove splashy some time down the road.

```
sudo dpkg-divert --package splashy --divert --remove /etc/lsb-base-logging.sh
```

Remember to read the man page for dpkg-divert. :)

---

### Post by saleenman on 2009-07-21
It WORKED!!!!!:D:D:D

Thank you all so much!!

P.S.-Since I'm only 14 my parents did not want me to join forums and talk to people. (They are a little overprotective.) I've been using Ubuntu for about a year and I like it much better than winblows.  So this was the first time that I had a problem that I couldn't fix. I was amazed at how many people are nice enough to help a total stranger.

Thank you all once again for your help!!!:D

---

### Post by rogerw05465 on 2009-08-13
> **michy99 said:**
> How about this```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.backup
sudo apt-get update
```
Hope yours got fixed. Mine did! See the thread on "package manager failure" for the history.

I had to go a couple of steps further that michy99 suggested., so the steps are outlined here:
- After running apt-get updates, I got an error that there was no status file
- I copied the status.backup to status, and of course had my original problem back
- I edited the status file and removed the section on the package I was having problems with, then saved it
- Presto Chango, Synaptic works again!

---

