---
title: "Trying to install Digikam on Karmic, in hospital"
date: 2010-04-13
forum: General Help
---

### Post by Gooserider on 2010-04-13
Not sure if this is in the right place, if not feel free to move to a better location...
 
Hello

I am a long time Linux user, mostly on Gentoo.  Due to a recent accident, I have ended up in a rehab hospital (Spaulding in Boston, MA) with a serious spinal cord injury.  In order to get me back online, some of my friends have purchased me a Lenovo SL500 laptop.  Because of limited time, and not wanting to overload the rather limited hospital wireless network provided for patients, I decided not to do Gentoo, but instead to give Kubuntu 9.10 a try in hopes that it would "just work" and get me a working install with a minimum of headaches, and do so quickly.  The results have been mixed at best..  The hospital environment, including the drugs they have me on, greatly limits the amount of time I can spend on investigating stuff myself, and a lot of the resources I would otherwise use, thus the early call for help... 

The base system has installed OK, but I've been having a great deal of trouble with trying to add additional software - currently Digikam is my biggest frustration
(I consider this a VITAL program, and do NOT want an alternative!)  

In my latest effort, I was pointed at [https://launchpad.net/~fboucault/+archive/ppa]("https://launchpad.net/%7Efboucault/+archive/ppa") which I followed, and got the following
```
atorrey@wandering:~$ sudo add-apt-repository ppa:fboucault/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv F3B775879A33045C369C2904C08FE65343334730 
gpg: requesting key 43334730 from hkp server keyserver.ubuntu.com                                                                
gpgkeys: HTTP fetch error 7: couldn't connect to host                                                                            
gpg: no valid OpenPGP data found.                                                                                                
gpg: Total number processed: 0                                                                                                   
atorrey@wandering:~$ sudo apt-get update                                                                                         
Get:1 http://security.ubuntu.com karmic-security Release.gpg [189B]                                                              
Get:2 http://us.archive.ubuntu.com karmic Release.gpg [189B]                                                                     
Get:3 http://ppa.launchpad.net karmic Release.gpg [307B]                                                                         
Ign http://ppa.launchpad.net karmic/main Translation-en_US                                                                       
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                                                                   
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                                                            
Get:4 http://archive.canonical.com karmic Release.gpg [189B]                                                                     
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                                                      
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US                                                             
Ign http://archive.canonical.com karmic/partner Translation-en_US                                                                
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                                                        
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US                                                               
Get:5 http://archive.canonical.com karmic Release [9,347B]                                                                       
Get:6 http://ppa.launchpad.net karmic Release [66.0kB]                                                                           
Ign http://archive.canonical.com karmic Release                                                                                  
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                                                      
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US                                                             
Get:7 http://security.ubuntu.com karmic-security Release [44.1kB]                                                                
Get:8 http://us.archive.ubuntu.com karmic-updates Release.gpg [189B]                                                             
Hit http://archive.canonical.com karmic/partner Packages                                                                         
Err http://security.ubuntu.com karmic-security Release                                                                           
                                                                                                                                 
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US                                                           
Hit http://archive.canonical.com karmic/partner Sources                                                                          
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US                                                     
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US                                                       
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US                                                     
Ign http://ppa.launchpad.net karmic Release                                                                                      
Get:9 http://us.archive.ubuntu.com karmic-backports Release.gpg [189B]                                                           
Get:10 http://ppa.launchpad.net karmic/main Packages [1,934B]                                                                    
Ign http://us.archive.ubuntu.com karmic-backports/main Translation-en_US                                                         
Ign http://us.archive.ubuntu.com karmic-backports/restricted Translation-en_US                                                   
Ign http://us.archive.ubuntu.com karmic-backports/universe Translation-en_US                                                     
Ign http://us.archive.ubuntu.com karmic-backports/multiverse Translation-en_US                                                   
Get:11 http://us.archive.ubuntu.com karmic Release [65.9kB]                                                                      
Err http://us.archive.ubuntu.com karmic Release                                                                                  
                                                                                                                                 
Get:12 http://us.archive.ubuntu.com karmic-updates Release [44.1kB]                                                              
Err http://us.archive.ubuntu.com karmic-updates Release                                                                          
                                                                                                                                 
Get:13 http://us.archive.ubuntu.com karmic-backports Release [37.1kB]                                                            
Get:14 http://us.archive.ubuntu.com karmic-backports/main Packages [67.7kB]                                                      
Get:15 http://us.archive.ubuntu.com karmic-backports/restricted Packages [14B]                                                   
Get:16 http://us.archive.ubuntu.com karmic-backports/universe Packages [20.7kB]                                                  
Get:17 http://us.archive.ubuntu.com karmic-backports/multiverse Packages [14B]                                                   
Get:18 http://us.archive.ubuntu.com karmic-backports/main Sources [24.8kB]                                                       
Get:19 http://us.archive.ubuntu.com karmic-backports/restricted Sources [14B]                                                    
Get:20 http://us.archive.ubuntu.com karmic-backports/universe Sources [5,196B]                                                   
Get:21 http://us.archive.ubuntu.com karmic-backports/multiverse Sources [14B]                                                    
Fetched 225kB in 3s (66.3kB/s)                                                                                                   
Reading package lists... Done                                                                                                    
W: GPG error: http://archive.canonical.com karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>                                                                             
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C08FE65343334730
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release

W: Some index files failed to download, they have been ignored, or old ones used instead.
atorrey@wandering:~$ apt-get install digikam
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
atorrey@wandering:~$ sudo apt-get install digikam
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  digikam: Depends: liblensfun0 (>= 0.2.3) but it is not installable
E: Broken packages
atorrey@wandering:~$

```HELP!

What do I need to do to be able to install basic software that IMHO SHOULD be part of an easy install, if not part of the basic system?

Gooserider

---

### Post by no2498 on 2010-04-14
fix the Broken packages
will help with the outcome 
system administration synaptic package manager fix Broken packages

hope this helps

---

### Post by Gooserider on 2010-04-16
> **no2498 said:**
> fix the Broken packages
will help with the outcome 
system administration synaptic package manager fix Broken packages

hope this helps

Not really - :(

I'm not at all familiar with Kubuntu, so I'm really not sure how to IDENTIFY the broken packages, let alone fix them.

Looking in the menu, I'm not finding anything labeled "synaptic" either (I thought that was a Ubuntu only thing, and that Kubuntu did something else?)  I am finding a "KPackage Kit" but all I can get it to do is list already installed packages, with the option of removing them - but nothing about installing new packages.

I'm afraid I need more "hand holding" than your brief response provides.

Gooserider

---

### Post by no2498 on 2010-04-16
click system administration synaptic package manager
fix broken packages

---

### Post by Gooserider on 2010-04-16
> **no2498 said:**
> click system administration synaptic package manager
fix broken packages

Couldn't find anything labeled synaptic.  When I went to settings / system settings, I saw an entry for "install/remove software packages that brought up a screen for software management that looked like the KPackage Kit that I mentioned earlier.

This time when I entered "digikam" it came back and said It found two packages, digikam, and digikam-dbg. I tried selecting first just Digikam, and then both, and in both cases it failed to install, with the DETAILED error message that it was unable to find dependencies for Digikam - with no data as to what the missing dependency is...:confused:

Gooserider

---

### Post by philip5 on 2010-04-22
If you are having problem with Digikam from that PPA then you could always try Digikam from my PPA instead. If you are using KDE 4.4.x then I would suggest that you use it from my kde44 PPA and if not then just my "extra" PPA. My PPA have all the packages that are needed if they are not in the official Ubuntu repositories and Ubuntu Universe.

You find info about my PPA if you follow the link in my signature.

Good luck and have fun!

---

### Post by Gooserider on 2010-08-08
Bringing back this thread from the dead, I think it is finally solved, though I am not sure what I did (if anything) to fix it...  I mentioned the difficulty I was having at our local Linux Meetup, and was told to open a bash window, and give the commands "sudo apt-get update" and "sudo apt-get upgrade" and tell what happened, with the expectation that failure would point to a problem.  However everything seemed to work OK, with a considerable number of programs being upgraded, followed by a reboot request.  After rebooting, the KDE package updater ran, with more stuff being updated, followed by yet another reboot request (Shades of Microsoft!) 

After that, I tried using the KDE package manager to install Digikam once more, and this time it worked perfectly far as I can tell...  It appeared to install, and put an Icon in the right place on the start menu.  When I clicked on that it ran a setup program and picked up the pictures I'd already gotten stored on the system and put them in an album, etc.

Don't know why it works now, and not earlier, but glad that it does...

Gooserider

---

