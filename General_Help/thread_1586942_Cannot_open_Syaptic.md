---
title: "Cannot open Syaptic"
date: 2010-10-02
forum: General Help
---

### Post by techiewannabe on 2010-10-02
I cannot open Synaptic Package Manager. I get the following message when I try (see attached):

Any help would be appreciated.

Thanks.

---

### Post by yetiman64 on 2010-10-02
> **techiewannabe said:**
> I cannot open Synaptic Package Manager. I get the following message when I try (see attached):

Any help would be appreciated.

Thanks.
Make sure Synaptic is closed first.
Goto System > Administration > Software Sources and goto the "Other Software" tab. If there are multiple entries for Canonical (Ticked), then detick or even remove one.
Reload the sources on closing Software Sources by choosing the reload button. 
Try and restart Synaptic.

---

### Post by barney385 on 2010-10-02
Go to your software sources list and remove the duplicate.

---

### Post by techiewannabe on 2010-10-02
yetiman64 and barney35:

Thanks for your suggestions. 

I realized, based on your suggestions, that one of the software sources was a duplicate. I deleted that duplicate. However, I did get the following message when I tried to update. (Please see the attached image.) Is it related to this problem or should I create a new thread?

techiewannabe

---

### Post by yetiman64 on 2010-10-02
> ...Is it related to this problem or should I create a new thread?
Sounds like a continuation of the first problem and is probably better left in this thread.

Try
```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post back if it shows any errors. Code is just an update done in terminal and may reset or affect the file mentioned in the error listed. If no errors occur  try reopening Synaptic then.

---

### Post by techiewannabe on 2010-10-02
yetiman64:
Thanks for your note.
Here is what I got when I cut and pasted your commands to the terminal.

[INDENT]mountlings@mountlings-compaq-laptop:~$ sudo apt-get update && sudo apt get upgrade
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Reading package lists... Done
sudo: apt: command not found
mountlings@mountlings-compaq-laptop:~$ 

[/INDENT]Thanks.

---

### Post by yetiman64 on 2010-10-02
```
> **techiewannabe said:**
> yetiman64:
Thanks for your note.
Here is what I got when I cut and pasted your commands to the terminal.[INDENT]mountlings@mountlings-compaq-laptop:~$ sudo apt-get update && sudo apt get upgrade
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Reading package lists... Done
sudo: apt: command not found
mountlings@mountlings-compaq-laptop:~$ 

[/INDENT]Thanks.
```Sorry the 2nd part of the code was wrong, can you try it again please, also it's good if you can wrap long output in code tags, thanks.

Edit: command should have been "**apt-get**" not "apt get" or "apt get-upgrade"

---

### Post by techiewannabe on 2010-10-02
Thanks yetiman64:

The problem continues. Here is the text that I received. (I'm not sure that I edited your command correctly.)

mountlings@mountlings-compaq-laptop:~$ sudo apt-get update && sudo apt-get
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
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
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Reading package lists... Done
apt 0.7.20.2ubuntu6 for i386 compiled on Apr 17 2009 04:25:29
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
                       This APT has Super Cow Powers.
mountlings@mountlings-compaq-laptop:~$ 


I appreciate your help.

By the way, where in Queensland do you live? I used to live in Melbourne. I love the land down under!

Techiewannabe

---

### Post by yetiman64 on 2010-10-02
> **techiewannabe said:**
> Thanks yetiman64:

The problem continues. Here is the text that I received. (I'm not sure that I edited your command correctly.)...

I appreciate your help.
By the way, where in Queensland do you live? I used to live in Melbourne. I love the land down under! 

Techiewannabe


Not quite, should be "sudo apt-get update && sudo apt-get  upgrade" (without the quotes), note, just copy and paste from the  original post with this code in, as I fixed it with an edit and is much  more accurate for you, when I actually get the code right that is [B]:smile:.
[/B]
<off topic>
No worries Techiewannabe (or should I say Hakuna Matata :biggrin:)
In the Far North of the state just south of Cairns - Yeah not a bad spot :wink:.</offtopic>

---

### Post by techiewannabe on 2010-10-02
yetiman64: 

Here are the results of the commands:

[PHP]mountlings@mountlings-compaq-laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for mountlings: 
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_US
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US      
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US    
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty-updates Release.gpg
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Hit http://archive.canonical.com jaunty Release                      
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://archive.ubuntu.com jaunty Release                        
Hit http://archive.ubuntu.com jaunty-updates Release                 
Hit http://archive.canonical.com jaunty/partner Sources              
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://archive.ubuntu.com jaunty/main Packages                   
Hit http://archive.ubuntu.com jaunty/universe Packages               
Hit http://archive.ubuntu.com jaunty/restricted Packages             
Hit http://archive.ubuntu.com jaunty/multiverse Packages             
Hit http://archive.canonical.com jaunty/partner Packages           [/PHP]Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adobe-flashplugin avahi-autoipd avahi-daemon avahi-utils bzip2 dpkg
  fglrx-modaliases libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-gobject0
  libavahi-ui0 libbz2-1.0 libgdiplus libssl0.9.8 openssl
19 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/11.3MB of archives.
After this operation, 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
mountlings@mountlings-compaq-laptop:~$

Thanks for your help.

<off topic: Yes, mate, you're in a great spot near Cairns!>

---

### Post by yetiman64 on 2010-10-02
Have a read of this --[thread--]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8656675") (particularly posts of drs305) and this [--post--]("http://ubuntuforums.org/showpost.php?p=7943852&postcount=6") (final fix for previous link and see if they help you. I got to the info by googling your exact error output. 

> dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
& good luck.

---

### Post by techiewannabe on 2010-10-03
yetiman64:
Thanks for the note.
I tried to follow the thread and used some of the suggestions. I'm afraid that the situation remains. :(

---

### Post by yetiman64 on 2010-10-03
> **techiewannabe said:**
> yetiman64:
Thanks for the note.
I tried to follow the thread and used some of the suggestions. I'm afraid that the situation remains. :(
Have patience and hopefully someone with more immediate experience with the problem may come along and help. Once again good luck with this. Cheers from yetiman64.

---

### Post by techiewannabe on 2010-10-03
Thanks, yetiman64.
We'll see what develops....

---

