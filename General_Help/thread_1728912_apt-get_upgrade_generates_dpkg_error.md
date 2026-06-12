---
title: "apt-get upgrade generates dpkg error"
date: 2011-04-14
forum: General Help
---

### Post by Rocket J Squirrel on 2011-04-14
For a couple months now, Update Manager has been unable to install a help file for LibreOffice. Here's what apt-get upgrade has to say about it:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libobasis3.3-en-us-help
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9,055kB of archives.
After this operation, 14.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 348977 files and directories currently installed.)
Preparing to replace libobasis3.3-en-us-help 3.3.0-17 (using .../libobasis3.3-en-us-help_3.3.2-19_i386.deb) ...
Unpacking replacement libobasis3.3-en-us-help ...
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb (--unpack):
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jackelliott@TheJackUbuntuNetbook:~$ 
```

It would be nice to put this issue to bed.

---

### Post by KegHead on 2011-04-14
Hi!

Try:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

You might be asked to restart

KegHead

---

### Post by Rocket J Squirrel on 2011-04-14
Thank you, KegHead

Alas, same errors every time. 

Why does my computer hate the LibreOffice help file?

---

### Post by matt_symes on 2011-04-14
Hi

Try deleting the file.
[FONT=monospace]
[/FONT]```
sudo rm /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb

```Then try again.
```

sudo apt-get update
sudo apt-get upgrade
```EDIT: After a second look at the issue, i'm not sure if this will work, but give it a try.

What does this return ?

```
dpkg -l | grep libobasis3.3-en-us-help
```

(Small L above)

Kind regards

---

### Post by Rocket J Squirrel on 2011-04-14
Thank you. Deleting the file didn't fix the problem, as you suspected:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo rm /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb
jackelliott@TheJackUbuntuNetbook:~$ ls /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb
ls: cannot access /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb: No such file or directory
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libobasis3.3-en-us-help
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 9,055kB of archives.
After this operation, 14.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://download.tuxfamily.org/gericom/libreoffice/  libobasis3.3-en-us-help 3.3.2-19 [9,055kB]
Fetched 9,055kB in 1min 30s (100kB/s)                                                                                                                      
(Reading database ... 348977 files and directories currently installed.)
Preparing to replace libobasis3.3-en-us-help 3.3.0-17 (using .../libobasis3.3-en-us-help_3.3.2-19_i386.deb) ...
Unpacking replacement libobasis3.3-en-us-help ...
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb (--unpack):
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jackelliott@TheJackUbuntuNetbook:~$ 
```

Your second suggestion:
```
jackelliott@TheJackUbuntuNetbook:~$ dpkg -l | grep libobasis3.3-en-us-help
ii  libobasis3.3-en-us-help                                              3.3.0-17                                          Language help module for LibreOffice 3.3, language en_US
jackelliott@TheJackUbuntuNetbook:~$ 
```

---

### Post by KegHead on 2011-04-14
Hi!

Do you think it would help to force upgrade?

sudo apt-get update

sudo apt-get upgrade -f

KegHead

---

### Post by KegHead on 2011-04-14
Hi!

I noticed you're getting libreoffice from tuxfamily?

KegHead

---

### Post by matt_symes on 2011-04-14
Hi

@KegHead

What about uninstalling libobasis3.3-en-us-help_3.3.0-17 and then installing libobasis3.3-en-us-help_3.3.0-19. What do you think the ramifications would be ?

Another option is to uninstall the whole app and reinstall at the newer version. Thoughts ?

It's not an app i use so......

Kind regards

---

### Post by bodhi.zazen on 2011-04-14
It looks like a poorly written .deb =)

You can try :

```
sudo mv /opt/libreoffice/basis3.3/help/en/sdraw.cfg /root
sudo apt-get -f
```

If that works, you can then:

```
sudo rm /root/sdraw.cfg
```

If it fails, move it back.

Either way, time to learn to file bug reports =)

---

### Post by Rocket J Squirrel on 2011-04-14
Hi all,

Really appreciate the help here. 

sudo mv /opt/libreoffice/basis3.3/help/en/sdraw.cfg /root
Generated no errors. 
But, 
```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get -f
apt 0.8.3ubuntu7 for i386 compiled on Oct  5 2010 14:07:36
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   markauto - Mark the given packages as automatically installed
   unmarkauto - Mark the given packages as manually installed

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers
```.

Assuming that we meant "sudo apt-get update -f", I tried that and:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo apt-get update -f
Get:1 http://dl.google.com stable Release.gpg [197B]                                                                                                       
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                                      
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                                                   
Get:2 http://dl.google.com stable Release.gpg [197B]                                                                                                       
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                                  
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US                                                                               
Get:3 http://dl.google.com stable Release [1,347B]                                                                                                         
Get:4 http://dl.google.com stable Release [1,347B]                                                                                                         
Get:5 http://extras.ubuntu.com maverick Release.gpg [72B]                                                                                                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                          
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                          
Ign http://ppa.launchpad.net/claws-mail/ppa/ubuntu/ maverick/main Translation-en                                                                           
Ign http://ppa.launchpad.net/claws-mail/ppa/ubuntu/ maverick/main Translation-en_US                                                                        
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                                               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                                               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                                                                            
Hit http://archive.canonical.com maverick Release.gpg                                                                                                      
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                                                   
Hit http://us.archive.ubuntu.com maverick Release.gpg                                                                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                                   
Get:6 http://download.tuxfamily.org  Release.gpg [198B]                                                                                                    
Hit http://packages.medibuntu.org maverick Release.gpg                                                                                                     
Get:7 http://dl.google.com stable/main i386 Packages [1,096B]                                                                                              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                                                                                
Hit http://archive.canonical.com maverick Release                                                                                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US                                                                      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US                                                                      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US                                                                        
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                                       
Hit http://extras.ubuntu.com maverick Release                                                                                                              
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                          
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en                                                                
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en_US                                                             
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                          
Ign http://ppa.launchpad.net/kilian/f.lux/ubuntu/ maverick/main Translation-en                                                                             
Ign http://ppa.launchpad.net/kilian/f.lux/ubuntu/ maverick/main Translation-en_US                                                                          
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                                                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                                                                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                                                                               
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                                                                                              
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en                                                                          
Hit http://security.ubuntu.com maverick-security Release                                                                                                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                              
Get:8 http://dl.google.com stable/main i386 Packages [737B]                                                                                                
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en                                                                                     
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en_US                                                   
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_US                                                                       
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                          
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en                                                               
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US                                                            
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                          
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en                                                      
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en_US                                                                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                                                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                                                          
Hit http://archive.canonical.com maverick/partner Sources                                                                                                  
Get:9 http://download.tuxfamily.org  Release [724B]                                                                                                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                                                                       
Hit http://us.archive.ubuntu.com maverick Release                                                                                                          
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                                                   
Ign http://packages.medibuntu.org/ maverick/free Translation-en                                                                                            
Get:10 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ maverick/main Translation-en                                                             
Hit http://security.ubuntu.com maverick-security/main Sources                                                                                              
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ maverick/main Translation-en_US                                                          
Hit http://ppa.launchpad.net maverick Release                                                                                                     
Hit http://ppa.launchpad.net maverick Release                                                                                                              
Hit http://us.archive.ubuntu.com maverick-updates Release                                                                                                  
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                                            
Ign http://download.tuxfamily.org  Packages                                                                                                                
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                                               
Hit http://security.ubuntu.com maverick-security/universe Sources                                                           
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                              
Hit http://security.ubuntu.com maverick-security/main i386 Packages                                              
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                                        
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                                          
Get:11 http://ppa.launchpad.net maverick Release [9,765B]                                                                              
Hit http://us.archive.ubuntu.com maverick/main Sources                                                                                          
Hit http://us.archive.ubuntu.com maverick/restricted Sources                                                                                    
Hit http://us.archive.ubuntu.com maverick/universe Sources                                                                                      
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                                                                                    
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                                                                                    
Ign http://download.tuxfamily.org  Packages                                                                                                     
Hit http://security.ubuntu.com maverick-security/universe i386 Packages                                                                         
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                 
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US                                                        
Hit http://ppa.launchpad.net maverick/main Sources                                                                                                   
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                                             
Hit http://ppa.launchpad.net maverick/main Sources                                                                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                       
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages                                                             
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages                                                               
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages                                                             
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                                                                 
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources                                                        
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources                                                          
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources                                                        
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages                                                        
Get:12 http://download.tuxfamily.org  Packages [8,362B]                                                                     
Hit http://ppa.launchpad.net maverick/main Sources                                                                                    
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                              
Hit http://ppa.launchpad.net maverick/main Sources                                                                                    
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages                                                            
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages                                        
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                                                   
Hit http://ppa.launchpad.net maverick/main i386 Packages                                             
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages                           
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en  
Get:13 http://ppa.launchpad.net maverick/main Sources [606B]                                          
Get:14 http://ppa.launchpad.net maverick/main i386 Packages [1,045B]                                  
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US                     
Hit http://packages.medibuntu.org maverick Release        
Hit http://packages.medibuntu.org maverick/free i386 Packages
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Fetched 26.0kB in 4s (6,215B/s)
Reading package lists... Done
```

Promising . . . so:
```
jackelliott@TheJackUbuntuNetbook:~$ sudo rm /root/sdraw.cfg
```

Returned no errors. 

But then, sudo apt-get upgrade did this:

```
<snip>
dpkg: error processing /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb (--unpack):
 trying to overwrite '/opt/libreoffice/basis3.3/help/en/sdraw.cfg', which is also in package libobasis3.3-en-us-draw 3.3.0-17
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libobasis3.3-en-us-help_3.3.2-19_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Learn to file bug reports seems the next step?

---

### Post by bodhi.zazen on 2011-04-14
Yep, it is broken =)

Lets try to remove it.

First, lets become root so we can run a few commands without entering sudo over and over ;)

```
sudo -i
``` 

Next, replace that deleted file with an empty file:

```
touch /opt/libreoffice/basis3.3/help/en/sdraw.cfg
```

Now remove the offending package if we can:

```
dpkg --remove --force-all libobasis3.3-en-us-help
```

Then run

```
apt-get install -f
```

If that fails, post the error message and I will tell you how another trick.

---

### Post by Rocket J Squirrel on 2011-04-15
Okay, let's do this.

<rolls up sleeves>

```
jackelliott@TheJackUbuntuNetbook:~$ sudo -i
[sudo] password for jackelliott: 
root@TheJackUbuntuNetbook:~# touch opt/libreoffice/basis3.3/help/en/sdraw.cfg
touch: cannot touch `opt/libreoffice/basis3.3/help/en/sdraw.cfg': No such file or directory
root@TheJackUbuntuNetbook:~# touch /opt/libreoffice/basis3.3/help/en/sdraw.cfg
root@TheJackUbuntuNetbook:~# dpkg --remove --force-all libobasis3.3-en-us-help
(Reading database ... 348976 files and directories currently installed.)
Removing libobasis3.3-en-us-help ...
root@TheJackUbuntuNetbook:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libtextcat-data-utf8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up google-chrome-beta (11.0.696.48-r81577) ...
Setting up vlc-data (1.1.4-1ubuntu1.5) ...
Setting up libvlccore4 (1.1.4-1ubuntu1.5) ...
Setting up libvlc5 (1.1.4-1ubuntu1.5) ...
Setting up vlc-nox (1.1.4-1ubuntu1.5) ...
Setting up vlc-plugin-notify (1.1.4-1ubuntu1.5) ...
Setting up vlc (1.1.4-1ubuntu1.5) ...
Setting up mozilla-plugin-vlc (1.1.4-1ubuntu1.5) ...
Setting up vlc-plugin-pulse (1.1.4-1ubuntu1.5) ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@TheJackUbuntuNetbook:~# apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]                                                                                            
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US                                                                        
Get:2 http://dl.google.com stable Release.gpg [197B]                                                                                            
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                       
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US                                                                    
Get:3 http://dl.google.com stable Release [1,347B]                                                                                              
Get:4 http://dl.google.com stable Release [1,347B]                                                                                              
Get:5 http://dl.google.com stable/main i386 Packages [1,096B]                                                                                   
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                                                                 
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                               
Ign http://ppa.launchpad.net/claws-mail/ppa/ubuntu/ maverick/main Translation-en                                                                
Ign http://ppa.launchpad.net/claws-mail/ppa/ubuntu/ maverick/main Translation-en_US                                                             
Hit http://extras.ubuntu.com maverick Release.gpg                                                                                               
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                               
Hit http://archive.canonical.com maverick Release.gpg                                                                                           
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                                        
Get:6 http://dl.google.com stable/main i386 Packages [737B]                                                                                     
Hit http://us.archive.ubuntu.com maverick Release.gpg                                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                           
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                        
Get:7 http://download.tuxfamily.org  Release.gpg [198B]                                                                                         
Hit http://packages.medibuntu.org maverick Release.gpg                                                                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US                                                             
Hit http://security.ubuntu.com maverick-security Release                                                                                        
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                               
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en                                                     
Ign http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/ maverick/main Translation-en_US                                                  
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                               
Ign http://ppa.launchpad.net/kilian/f.lux/ubuntu/ maverick/main Translation-en                                                                  
Ign http://ppa.launchpad.net/kilian/f.lux/ubuntu/ maverick/main Translation-en_US                                                               
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                               
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                            
Hit http://extras.ubuntu.com maverick Release                                                                                                   
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                                                                     
Hit http://archive.canonical.com maverick Release                                                                                               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                                                                    
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                                                                                   
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en                                                               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                                                
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en                                                                          
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en_US                                                                       
Ign http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ maverick/main Translation-en_US                                                            
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                      
Hit http://security.ubuntu.com maverick-security/main Sources                                                                                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                             
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en                                                    
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_US                                                 
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                               
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en                                                               
Ign http://ppa.launchpad.net/postler-dev/ppa/ubuntu/ maverick/main Translation-en_US                                                            
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                                                   
Hit http://us.archive.ubuntu.com maverick Release                                                                                      
Hit http://archive.canonical.com maverick/partner Sources                                                                                       
Get:8 http://download.tuxfamily.org  Release [724B]                                                                                             
Ign http://packages.medibuntu.org/ maverick/free Translation-en                                                                                 
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                               
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ maverick/main Translation-en                                                  
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                                             
Hit http://security.ubuntu.com maverick-security/universe Sources                                                                               
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                                                             
Hit http://security.ubuntu.com maverick-security/main i386 Packages                                                                             
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                                                                       
Hit http://security.ubuntu.com maverick-security/universe i386 Packages                                                                         
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                                       
Ign http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/ maverick/main Translation-en_US                                               
Hit http://ppa.launchpad.net maverick Release                                                                                                   
Hit http://ppa.launchpad.net maverick Release                                                                                                   
Hit http://us.archive.ubuntu.com maverick-updates Release                                                                                       
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                                 
Ign http://download.tuxfamily.org  Packages                                                                                                     
Hit http://ppa.launchpad.net maverick Release                                              
Hit http://ppa.launchpad.net maverick Release                        
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://ppa.launchpad.net maverick Release                                                                    
Hit http://us.archive.ubuntu.com maverick/main Sources                                                           
Hit http://us.archive.ubuntu.com maverick/restricted Sources                                                     
Hit http://us.archive.ubuntu.com maverick/universe Sources                                 
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                               
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                               
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages                         
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages                           
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US                                               
Ign http://download.tuxfamily.org  Packages                                                                                 
Hit http://ppa.launchpad.net maverick/main Sources                                                                          
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                    
Hit http://ppa.launchpad.net maverick/main Sources                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                    
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                                                              
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources                                                        
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources                                                          
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources                                                        
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages                                                        
Get:9 http://download.tuxfamily.org  Packages [8,362B]                                                                      
Hit http://ppa.launchpad.net maverick/main Sources                                                                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                                            
Hit http://ppa.launchpad.net maverick/main Sources                            
Hit http://ppa.launchpad.net maverick/main i386 Packages                      
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages    
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages      
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages    
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en           
Hit http://ppa.launchpad.net maverick/main Sources                            
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                       
Hit http://ppa.launchpad.net maverick/main Sources                                                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                       
Hit http://ppa.launchpad.net maverick/main Sources                                                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                       
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US                                         
Hit http://packages.medibuntu.org maverick Release        
Hit http://packages.medibuntu.org maverick/free i386 Packages
Hit http://packages.medibuntu.org maverick/non-free i386 Packages
Fetched 14.2kB in 4s (3,430B/s)
Reading package lists... Done
root@TheJackUbuntuNetbook:~# 
```

Wow, nary an error in sight!

And lookit all them other packages that were installed. Were they stacked up behind the libobasis help file, waiting for it to go in before they could install?

Lemme run Update Manager and see if it's happy now . . . hang on . . . *no updates to install.*

Fixed it, man. Thank you!

---

### Post by bodhi.zazen on 2011-04-15
Looks good at the moment =)

You might want to run:

```
sudo apt-get autoremove
```

---

### Post by Rocket J Squirrel on 2011-04-15
Okee doke. 
```
root@TheJackUbuntuNetbook:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libtextcat-data-utf8
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 254kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 348945 files and directories currently installed.)
Removing libtextcat-data-utf8 ...
root@TheJackUbuntuNetbook:~# 
```

Looks good to me. Marking this thread SOLVED in one, two, three . . .

---

### Post by KegHead on 2011-04-15
Hi!

Try:

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

KegHead

---

### Post by Rocket J Squirrel on 2011-04-15
Thanks, KegHead

```
root@TheJackUbuntuNetbook:~# apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@TheJackUbuntuNetbook:~# apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Looks clean.

---

### Post by KegHead on 2011-04-15
Congrats!

KegHead

---

### Post by bodhi.zazen on 2011-04-15
Hate it when apt-get breaks, glad it is working now =)

FYI: Step 3 would have been manual package removal and another arcane apt-get command.

I have a blog post here, but it is a bit brief and may or man not be technobabble depending on your experience with apt-get ;)

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

