---
title: "Synaptic and Update Manager Won't Load"
date: 2010-09-18
forum: General Help
---

### Post by techiewannabe on 2010-09-18
I am unable to open either the Synaptic program or the Update Manager. 

I believe that this may be due to the fact that my ISP was interrupted for about 15 minutes and it could've effected the updates that were in progress. (Prior to the updates, my system was running fine.)

I get the following messages shown below. 

Your help would be appreciated.

Thanks in advance.

---

### Post by wilee-nilee on 2010-09-18
Try these two commands in the terminal.
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f 
``` 

These may fix this lock and continue the update/upgrade, but they also may just make so you can get into synaptic to look for any problems. 

You also want to really specific whether it was the update or upgrade portion in general, so that we can have the best possible information.;)

---

### Post by techiewannabe on 2010-09-18
Wilee-nilee:
Thanks for your suggestions. Unfortunately, the situation remains the same. 
Per your comment, I want to emphasize that the process underway was an update (not an upgrade).
Here is the text I received when I tried to commands you suggested.
Thanks.

[INDENT]mountlings@mountlings-compaq-laptop:~$ sudo dpkg --configure -a
[sudo] password for mountlings: 
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Input/output error
mountlings@mountlings-compaq-laptop:~$ sudo apt-get install -f
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
mountlings@mountlings-compaq-laptop:~$ 
[/INDENT]

---

### Post by wilee-nilee on 2010-09-18
This is an area that I'm just not fluent in as I rarely have had a problem.

Have you tried to reboot and choose the recovery from grub and then run fix broken packages. This is what I would do but like I said I have limited knowledge in these lockups.

Also upgrade doesn't men your upgrading the distro. To get the latest packages in a ubuntu os you run
sudo apt-get update      
then to install any new packages
sudo apt-get upgrade    

I was just referring to knowing which was running

---

### Post by drs305 on 2010-09-18
Normally there is a "Merge List" error message for the following to work, but if there is a list problem you might try the following.

Open Synaptic or Software Sources, note your selected repositories, and then untick them all. Do the same for the Third Party repositories. 

This should clear the lists and if you reselect them it and then try to update the lists it may restore uncorrupted ones which will work.

---

### Post by techiewannabe on 2010-09-19
Wili-nilee and DRS305:

Thanks for your notes. I don't really know how to navigate around GRUB, yet, but will try to read some of the articles that were linked to DRS305's page. I did try to remove, then replace, all of the software sources, but that didn't resolve the problem. 

I'll try to learn more about GRUB, but am open to other ideas as well.

Thanks.

---

### Post by jmszr on 2010-09-19
techiewannabe,

I had a similar problem and this command fixed it for me:

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by drs305 on 2010-09-19
The links to Grub won't really help you in this situation, other than to learn something about Grub2 and to access the recovery mode (which should be an option on the Grub 2 menu). This is an APT problem, which is the package manager. The only reason Grub was referenced was to be able to get to the recovery mode.

Deselecting and then adding the repositories was one thing to try to fix list corruption. The other part of the error messages mentions the 'status' list. 

There is a backup status list that we can try to invoke. Often it ends up containing the same errors, but it's worth trying. Since it's a system file we will use 'sudo' to run commands as root. 

Type or copy the commands prior to the #. The # and text afterward are just telling you what the command does.

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad # rename *status* file
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status # copy *status* backup file and name it *status*  
sudo apt-get update  # see if problem is solved
```

If the problem still remains, restore *status* file to original:
```
sudo cp /var/lib/dpkg/status.bad /var/lib/dpkg/status
```

---

### Post by techiewannabe on 2010-09-19
jmscr and drs305:

Thanks to each of you for your suggestions.

Jmscr, I copied and pasted your suggestion but it didn't remedy the situation. 

Drs305, per your suggestion, I copied the commands you suggested and it worked perfectly! I have no idea why it worked! Is there a link, or reading, you could direct me towards so I might understand what worked?

Again, thanks to each of you.

---

### Post by drs305 on 2010-09-19
> **techiewannabe said:**
> 
Drs305, per your suggestion, I copied the commands you suggested and it worked perfectly! I have no idea why it worked! Is there a link, or reading, you could direct me towards so I might understand what worked?

Again, thanks to each of you.

One of the many good things about linux is that the terminal often gives you an idea of what the problem is. Your error message was:
> E: The package lists or status file could not be parsed or opened.

APT is the package manager which keeps track of what is installed and what is available. When you tried to update things, APT reported the error saying that it couldn't get the information it needed to process the request. Things that it needs to be able to read include the 1) package lists, which are the lists in /var/lib/apt/lists which show what packages are contained in the repositories; and 2) the "lists" file which contains information about each package and the install status of these packages.

Somehow one of these files became corrupted. The first suggestion I gave would have removed all the package lists and downloaded new ones. If there had been a problem with one of the package lists, that should have fixed it.

Since that didn't work, we moved on to a possibly bad "status" file. APT keeps a backup copy called "status-old" which hopefully won't get corrupted if the main file does. It appears in your case that the status-old file was usable, and so when you renamed it APT found the data it could use.

As far as learning how things work, my learning has been just via trial and mostly error. As I've had problems, I've learned from others how to fix them. Fortunately, one of the benefits of the linux error messages is that they are fairly standard. One of the best ways to find solutions, as well as explanations of what is going on, is to do an internet search using the exact terminology. Usually you can find enough hits to help you out.

---

### Post by techiewannabe on 2010-09-19
DRS305:
Thanks for your note. 
Unfortunately, for no apparent reason, the problem is back! Here are the results of the commands:

[INDENT]mountlings@mountlings-compaq-laptop:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad # rename status file
[sudo] password for mountlings: 
mountlings@mountlings-compaq-laptop:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad # rename status file
mv: cannot stat `/var/lib/dpkg/status': No such file or directory
mountlings@mountlings-compaq-laptop:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status # copy status backup file and name it status  
mountlings@mountlings-compaq-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
mountlings@mountlings-compaq-laptop:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad # rename status file
mountlings@mountlings-compaq-laptop:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status # copy status backup file and name it status  
mountlings@mountlings-compaq-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
mountlings@mountlings-compaq-laptop:~$ sudo cp /var/lib/dpkg/status.bad /var/lib/dpkg/status
mountlings@mountlings-compaq-laptop:~$ sudo cp /var/lib/dpkg/status.bad /var/lib/dpkg/status
mountlings@mountlings-compaq-laptop:~$ 

[/INDENT]Thanks for your comments about the command line.

Other ideas with this problem?

Thanks.

---

### Post by drs305 on 2010-09-19
Is this how your original problem started, or is this different? 

Try changing servers via Software Sources or Synaptic. You might try the first corrective option again - deselecting and reselecting the repositories. 

Also, a note that Jaunty is about to reach it's End of Life. At some point next month the repositories will no longer be available at the current address. You should probably update to Karmic or do a clean install to a newer release before Jaunty's EOL. Here is a link regarding release dates:
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by techiewannabe on 2010-09-19
DRS305:

Thanks again for your help. Changing the software source solved the problem!

I appreciate your comments about the EOL for Jaunty. I am concerned about it, too. About a month and a half ago I tried to install Lucid but had a lot of trouble with it and couldn't resolve the problems. I got messages indicating that my install was unstable and that it was a partial install. Out of frustration, or ignorance, I uninstalled Lucid and went back to using Jaunty. I had posted my concerns but couldn't seem to find a solution to my difficulties. 

Has Karmic proved to be a pretty stable system? I might try that. 

Thanks again for your help.

---

### Post by drs305 on 2010-09-19
Yes, Karmic is pretty stable, although I'd recommend you give Lucid another try. Lucid 10.04.1 is now out and may resolve whatever issue you had the first time around. 

If you have the space (it really doesn't take much), you could always install it on another partition and have both Jaunty and Lucid for a time. A clean install of Lucid on a new partition would let you see if you can get it running while you would still have Jaunty as a backup or as you get Lucid set up the way you want.

Of course, doing an online upgrade from Jaunty to Karmic couldn't be much easier (for the next 6 months, when K reaches EOL).  :-)

---

### Post by techiewannabe on 2010-09-19
Thanks, DRS305:
Yeah...I think I'll take your suggestion. I've got plenty of hard drive space and had been considering partitioning it and devoting some of it to Lucid. I could give it another try.
Thanks for all of your help.

---

