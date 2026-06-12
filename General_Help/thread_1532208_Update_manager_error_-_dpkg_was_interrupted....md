---
title: "Update manager error - dpkg was interrupted..."
date: 2010-07-16
forum: General Help
---

### Post by jaconat on 2010-07-16
Hi

I keep getting the following error when the Update Manager runs.

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

If I open up a terminal and run ***sudo dpkg --configure -a*** I then get the following error.

```
dpkg: parse error, in file `/var/lib/dpkg/updates/0002' near line 1:
 newline in field name `

```

Any ideas how to fix this as I can't install any updates.

Many thanks

---

### Post by robsoles on 2010-07-16
I've a simple enough idea that will probably fix this for you but I want to see something first.

It's a little risky as far as I'm concerned because I can't be sure I am testing what I am going to tell you to do against EXACTLY your circumstances but I'm pretty sure it will work out for you.

Open terminal and type in **[COLOR=Red](Aug 2011: Don't follow these instructions without following the instructions in post #4 below!)[/COLOR]**
```
sudo mv /var/lib/dpkg/updates /root/
```If that doesn't report errors or you not being allowed then try the next **[COLOR=Red](Do #4 instructions now ;))[/COLOR]**
```
sudo apt-get update
```and if no errors are reported again then
```
sudo apt-get upgrade
```If you get no errors then your system just successfully updated and you can do the following but [COLOR=Red]don't do it if you got any errors at all at previous steps![/COLOR]
```
sudo 'rm -Rf /root/updates/*'
rmdir /root/updates
```and get on with your life. [COLOR=Red]BUT very important you get 'sudo rm ...' line exactly right or it can make big trouble like wiping out WHERE-EVER in your filesystem you point it!!![/COLOR]


If you get errors at any step DON'T EXECUTE THE NEXT STEP but instead post back the errors into this thread please.

---

### Post by jaconat on 2010-07-16
Hey Rob, many thanks for the quick reply.  I have posted below the results of the 3 commands.

As you can see the first command ran ok.  The second command produced an error about a missing public key - this error always occured even in update manager so I continued with the third command which gave the final error.  What do you think?  Run the sudo rm... command?

Thanks Dominic

```
dominic@ubuntu:~$ sudo mv /var/lib/dpkg/updates /root/
[sudo] password for dominic: 
dominic@ubuntu:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB                 
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Get: 1 http://security.ubuntu.com jaunty-security Release.gpg [189B]           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB          
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_GB                     
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_GB              
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB           
Get: 2 http://gb.archive.ubuntu.com jaunty-updates Release.gpg [189B]          
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Hit http://archive.ubuntu.com jaunty Release                                   
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB    
Get: 3 http://security.ubuntu.com jaunty-security Release [57.9kB]             
Get: 4 http://packages.medibuntu.org jaunty Release.gpg [197B]                 
Ign http://packages.medibuntu.org jaunty/free Translation-en_GB                
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_GB                     
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://archive.canonical.com jaunty Release                                
Hit http://gb.archive.ubuntu.com jaunty Release                                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_GB            
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_GB              
Get: 5 http://packages.medibuntu.org jaunty Release [11.7kB]                   
Get: 6 http://gb.archive.ubuntu.com jaunty-updates Release [57.9kB]            
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://wine.budgetdedicated.com jaunty Release                             
Hit http://archive.ubuntu.com jaunty/main Sources                              
Ign http://packages.medibuntu.org jaunty Release                               
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://archive.canonical.com jaunty/partner Packages                       
Hit http://archive.ubuntu.com jaunty/restricted Sources                        
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://ppa.launchpad.net jaunty/main Sources                               
Hit http://ppa.launchpad.net jaunty/main Packages                              
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://ppa.launchpad.net jaunty/main Sources                               
Get: 7 http://security.ubuntu.com jaunty-security/main Packages [165kB]        
Hit http://gb.archive.ubuntu.com jaunty/main Packages                          
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://gb.archive.ubuntu.com jaunty/main Sources                           
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources                     
Hit http://gb.archive.ubuntu.com jaunty/universe Sources                       
Hit http://gb.archive.ubuntu.com jaunty/universe Packages                      
Hit http://wine.budgetdedicated.com jaunty/main Packages                       
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages                    
Get: 8 http://gb.archive.ubuntu.com jaunty-updates/restricted Packages [2590B] 
Get: 9 http://gb.archive.ubuntu.com jaunty-updates/main Packages [243kB]       
Hit http://packages.medibuntu.org jaunty/non-free Packages                     
Get: 10 http://security.ubuntu.com jaunty-security/restricted Packages [2590B] 
Get: 11 http://security.ubuntu.com jaunty-security/restricted Sources [615B] 
Get: 12 http://security.ubuntu.com jaunty-security/main Sources [44.4kB]     
Get: 13 http://security.ubuntu.com jaunty-security/multiverse Sources [581B]   
Get: 14 http://security.ubuntu.com jaunty-security/universe Sources [25.9kB]
Get: 15 http://security.ubuntu.com jaunty-security/universe Packages [96.2kB]  
Get: 16 http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages [9575B]
Get: 17 http://gb.archive.ubuntu.com jaunty-updates/universe Packages [129kB]  
Get: 18 http://security.ubuntu.com jaunty-security/multiverse Packages [1999B] 
Fetched 850kB in 4s (209kB/s)                                                  
Reading package lists... Done
[B]W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems[/B]
dominic@ubuntu:~$ 
dominic@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  acroread ghostscript ghostscript-x libgs8 libpng12-0 libvte-common libvte9 python-vte sudo
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.4MB/67.6MB of archives.
After this operation, 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
Get: 1 http://archive.canonical.com jaunty/partner acroread 9.3.3-1jaunty1 [63.4MB]
Get: 2 http://security.ubuntu.com jaunty-security/main libpng12-0 1.2.27-2ubuntu2.2 [167kB]
Get: 3 http://security.ubuntu.com jaunty-security/main ghostscript 8.64.dfsg.1-0ubuntu8.1 [794kB]
Get: 4 http://security.ubuntu.com jaunty-security/main libgs8 8.64.dfsg.1-0ubuntu8.1 [2326kB]                                         
Get: 5 http://security.ubuntu.com jaunty-security/main ghostscript-x 8.64.dfsg.1-0ubuntu8.1 [66.4kB]                                  
Get: 6 http://security.ubuntu.com jaunty-security/main libvte-common 1:0.20.0-0ubuntu2.1 [34.1kB]                                     
Get: 7 http://security.ubuntu.com jaunty-security/main libvte9 1:0.20.0-0ubuntu2.1 [578kB]                                            
Get: 8 http://security.ubuntu.com jaunty-security/main python-vte 1:0.20.0-0ubuntu2.1 [29.9kB]                                        
Fetched 67.4MB in 4min 51s (232kB/s)                                                                                                  
Preconfiguring packages ...
[B]dpkg: cannot scan updates directory `/var/lib/dpkg/updates/': No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]

```

---

### Post by robsoles on 2010-07-16
NO.

```
sudo mkdir /var/lib/dpkg/updates
sudo chmod 755 /var/lib/dpkg/updates
```and start again from 'apt-get update' command, see how that goes - post back new errors etc.


EDIT: I don't know what's happened to that signature key but ignore that error for the purpose of this fix for now.

---

### Post by jaconat on 2010-07-16
No errors this time and results look much more positive than the first time.  I've posted results below just to be sure.  What do you think, safe to run sudo rm command now?

Thanks

```

dominic@ubuntu:~$ sudo mkdir /var/lib/dpkg/updates
[sudo] password for dominic: 
dominic@ubuntu:~$ sudo chmod 755 /var/lib/dpkg/updates
dominic@ubuntu:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com jaunty Release.gpg
Hit http://gb.archive.ubuntu.com jaunty/main Translation-en_GB                 
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_GB                     
Hit http://archive.canonical.com jaunty Release.gpg                            
Ign http://archive.canonical.com jaunty/partner Translation-en_GB              
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_GB          
Hit http://archive.ubuntu.com jaunty Release.gpg                               
Hit http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB           
Hit http://gb.archive.ubuntu.com jaunty-updates Release.gpg                    
Ign http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB   
Ign http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB     
Get: 1 http://packages.medibuntu.org jaunty Release.gpg [197B]                 
Ign http://packages.medibuntu.org jaunty/free Translation-en_GB                
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_GB            
Hit http://ppa.launchpad.net jaunty Release.gpg                                
Ign http://ppa.launchpad.net jaunty/main Translation-en_GB                     
Hit http://ppa.launchpad.net jaunty Release                                    
Hit http://archive.ubuntu.com jaunty Release                                   
Hit http://gb.archive.ubuntu.com jaunty Release                                
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_GB    
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_GB      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com jaunty-security Release                         
Hit http://archive.canonical.com jaunty Release                                
Hit http://wine.budgetdedicated.com jaunty Release.gpg                         
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_GB              
Hit http://gb.archive.ubuntu.com jaunty-updates Release                        
Hit http://ppa.launchpad.net jaunty Release                                    
Get: 2 http://packages.medibuntu.org jaunty Release [11.7kB]                   
Hit http://wine.budgetdedicated.com jaunty Release                        
Hit http://ppa.launchpad.net jaunty/main Packages                         
Hit http://ppa.launchpad.net jaunty/main Sources                          
Hit http://archive.ubuntu.com jaunty/main Sources                   
Hit http://gb.archive.ubuntu.com jaunty/main Packages               
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://gb.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://gb.archive.ubuntu.com jaunty/main Sources                           
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://archive.canonical.com jaunty/partner Packages                       
Hit http://gb.archive.ubuntu.com jaunty/multiverse Sources           
Hit http://gb.archive.ubuntu.com jaunty/universe Sources            
Hit http://gb.archive.ubuntu.com jaunty/universe Packages           
Hit http://gb.archive.ubuntu.com jaunty/multiverse Packages         
Hit http://security.ubuntu.com jaunty-security/restricted Packages  
Hit http://security.ubuntu.com jaunty-security/restricted Sources   
Hit http://security.ubuntu.com jaunty-security/main Sources         
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Packages 
Hit http://gb.archive.ubuntu.com jaunty-updates/main Packages        
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages  
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages    
Hit http://security.ubuntu.com jaunty-security/multiverse Sources    
Hit http://security.ubuntu.com jaunty-security/universe Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages   
Hit http://security.ubuntu.com jaunty-security/multiverse Packages 
Hit http://ppa.launchpad.net jaunty/main Packages                     
Ign http://packages.medibuntu.org jaunty Release                      
Ign http://wine.budgetdedicated.com jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://wine.budgetdedicated.com jaunty/main Packages
Hit http://packages.medibuntu.org jaunty/non-free Packages
Fetched 11.9kB in 1s (11.8kB/s)                          
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
dominic@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  acroread ghostscript ghostscript-x libgs8 libpng12-0 libvte-common libvte9
  python-vte sudo
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/67.6MB of archives.
After this operation, 81.9kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 259677 files and directories currently installed.)
Preparing to replace libpng12-0 1.2.27-2ubuntu2.1 (using .../libpng12-0_1.2.27-2ubuntu2.2_i386.deb) ...
Unpacking replacement libpng12-0 ...
Preparing to replace ghostscript 8.64.dfsg.1-0ubuntu8 (using .../ghostscript_8.64.dfsg.1-0ubuntu8.1_i386.deb) ...
Cleaning up font configuration of gs...
Cleaning up category psprint..
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category gsfontderivative..
Cleaning up category type3..
Cleaning up category type1..
Unpacking replacement ghostscript ...
Preparing to replace libgs8 8.64.dfsg.1-0ubuntu8 (using .../libgs8_8.64.dfsg.1-0ubuntu8.1_i386.deb) ...
Unpacking replacement libgs8 ...
Preparing to replace ghostscript-x 8.64.dfsg.1-0ubuntu8 (using .../ghostscript-x_8.64.dfsg.1-0ubuntu8.1_i386.deb) ...
Unpacking replacement ghostscript-x ...
Preparing to replace libvte-common 1:0.20.0-0ubuntu2 (using .../libvte-common_1%3a0.20.0-0ubuntu2.1_all.deb) ...
Unpacking replacement libvte-common ...
Preparing to replace libvte9 1:0.20.0-0ubuntu2 (using .../libvte9_1%3a0.20.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement libvte9 ...
Preparing to replace python-vte 1:0.20.0-0ubuntu2 (using .../python-vte_1%3a0.20.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement python-vte ...
Preparing to replace sudo 1.6.9p17-1ubuntu3.2 (using .../sudo_1.6.9p17-1ubuntu3.3_i386.deb) ...
Unpacking replacement sudo ...
Preparing to replace acroread 9.3.2-jaunty1 (using .../acroread_9.3.3-1jaunty1_i386.deb) ...
Unpacking replacement acroread ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up libpng12-0 (1.2.27-2ubuntu2.2) ...

Setting up libgs8 (8.64.dfsg.1-0ubuntu8.1) ...

Setting up ghostscript (8.64.dfsg.1-0ubuntu8.1) ...
Updating font configuration of gs...
Cleaning up category psprint..
Cleaning up category cmap..
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category gsfontderivative..
Cleaning up category type3..
Cleaning up category type1..
Updating category type1..
Updating category type3..
Updating category gsfontderivative..
Updating category truetype..
Updating category cid..
Updating category cmap..
Updating category psprint..
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.

Setting up ghostscript-x (8.64.dfsg.1-0ubuntu8.1) ...
Setting up libvte-common (1:0.20.0-0ubuntu2.1) ...
Setting up libvte9 (1:0.20.0-0ubuntu2.1) ...

Setting up python-vte (1:0.20.0-0ubuntu2.1) ...

Setting up sudo (1.6.9p17-1ubuntu3.3) ...

Setting up acroread (9.3.3-1jaunty1) ...
No LSB modules are available.
No LSB modules are available.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
dominic@ubuntu:~$ 

```

---

### Post by robsoles on 2010-07-16
Yes. Now it entirely looks fixed we can afford to ditch the copy of 'updates' from /root/ that has the broken files in it.

Goto [http://medibuntu.org/](http://medibuntu.org/) and have a look around, they may tell you where/how to get the correct signature key for their repository.

---

### Post by jaconat on 2010-07-19
Hi Rob, you are a star.  All working.  Thanks very much for your help.

---

### Post by robsoles on 2010-07-19
Very welcome, please consider marking this thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") using the 'thread tools' above.

---

### Post by Dorie on 2011-08-11
Hey guys, I was wondering if you could help me out with a very similar problem?  I attempted to follow the instructions here, and unfortunately got an error message right after the first command:

dorie@dorie-laptop:~$ sudo mv /var/lib/dpkg/updates /root/
[sudo] password for dorie: 
mv: cannot stat `/var/lib/dpkg/updates': No such file or directory
dorie@dorie-laptop:~$ 


I'm not much of a computer programmer, so I'm not sure how to proceed.  I can tell you what led up to this: a typical update via the update manager was cut short when my internet connection failed.  It had finished downloading components, and was in the update process when the connection failed- I had the "details" window expanded, and it stopped around 59% in whatever it was doing- and after reestablishing the connection it wouldn't budge.  So I rebooted- probably my first mistake.

After that I did an internet search and found this thread.  :)  I've also noticed that when opening the update manager, the window does a check for updates, then immediately closes again, which is new.  Also, Firefox is telling me that I need to update my adobe flash player if I want to play youtube files- which tells me one of the updates was probably flash related and there's a corrupted file there now?  

Anywho, any help would be greatly appreciated!
Dorie

edit: er, I also am certain there were "security updates" included this time around, of the type that require a reboot to completely update properly.

---

### Post by robsoles on 2011-08-12
(Welcome to UF)

If you haven't already started a thread of your own for this then consider a possible title after reading the following, make one, post back here with a link to it :)


You have a different problem, it may be that at some or other level it looks like jaconat's problem but at the relevant level it mustn't be or that command would have succeeded (or failed for a different reason). The next commands get you the info we can use to fix your updating problem...> **robsoles said:**
> ...

Open terminal and type in
..

```
sudo apt-get update
```and if no errors are reported again then
```
sudo apt-get upgrade
```If you get no errors then your system just successfully updated and you ...

...

If you get errors at any step DON'T EXECUTE THE NEXT STEP but instead post back the errors into this thread please.

Do those bits, obey the instructions and don't upgrade if update has error response; Pick a title from what seems the most relevant snippet of whatever error(s) you get back, start a new thread with that title, use [noparse]```
paste-terminal-copy-here
```[/noparse] to post the entire output of the first command to give you errors - if you revisit this thread to post a link to your new thread I will be alerted; On the other hand what with being a new thread without '[SOLVED]' in it's title might attract any number of people who can solve it even more efficiently (and assuredly) than I can.

:)

---

### Post by Dorie on 2011-08-13
Hey,

thanks for the reply!  I actually tried both commands just now (update and upgrade) in the order stated- and this time they both appeared to work!  That said, I then opened the update manager and it still has the same problem, as well as the flash player not working.  

So...I'll post the error message I got previously in another new thread as you suggested. :)  Thank you!

---

### Post by Dorie on 2011-08-13
Hi again!  Here's the (rather clumsy) thread I started:

[http://ubuntuforums.org/showthread.php?p=11146654#post11146654](http://ubuntuforums.org/showthread.php?p=11146654#post11146654)

Thanks again!

Dorie

---

