---
title: "Reading package lists...Error! --&gt; Help needed.Please."
date: 2010-09-07
forum: General Help
---

### Post by maizuddin35 on 2010-09-07
I have encounter this problem, one thing i had done is, increase the cache size. But still , this problem occur. 

adibmobile@empatbelas:~$ sudo apt-get check
Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 8388608. (man 5 apt.conf)
E: Error occurred while processing libnotify0.4-cil (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/my.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

---

### Post by maizuddin35 on 2010-09-08
is this sort of bug or something?

---

### Post by maizuddin35 on 2010-09-08
```
E: Problem with MergeList /var/lib/apt/lists/my.archive.ubuntu.com_ubuntu_dists_lucid_universe_ binary-i386_Packages

```

how can I actually deal with this part of the system?
do I need to delete it? or edit it?
I see it on my /lists/then...?

---

### Post by drs305 on 2010-09-08
> **maizuddin35 said:**
> 
how can I actually deal with this part of the system?
do I need to delete it? or edit it?
I see it on my /lists/then...?

There is probably a problem with the list(s) which contain the available packages. To fix this:

Open Software Sources or Synaptic (System, Administration ...). Then go to Settings, Repositories. Untick the "universe" repository. Technically, you should be able to immediately reselect it, but I'd reload the repository via the Synaptic main menu and then reselect it.

If you are having multiple "Merge list" errors or the above doesn't fix it, deselect all repositories that are enabled/ticked, reload, then reselect them. Write down which ones are selected if you have a bad memory, and don't forget to do the same with the ones in the "Other Software/Third Party" tab.

---

### Post by maizuddin35 on 2010-09-08
thanks for the reply, another problem...I cant get into synaptic. is there any way around? if I want to get into synaptic a window will appear showing the error.

---

### Post by plucky on 2010-09-09
> **maizuddin35 said:**
> thanks for the reply, another problem...I cant get into synaptic. is there any way around? if I want to get into synaptic a window will appear showing the error.


Open **Software Sources** or Synaptic (System, Administration ...).

---

### Post by drs305 on 2010-09-09
> **maizuddin35 said:**
> thanks for the reply, another problem...I cant get into synaptic. is there any way around? if I want to get into synaptic a window will appear showing the error.


There are the two files you might need to fix, and there are several steps.

1. In answer to your question, if you can't refresh the list via Synaptic, you can open Nautilus as root and delete the corrupted file manually. 

```
gksu nautilus /var/lib/apt/lists
```
Find the correct file and delete it.
*my.archive.ubuntu.com_ubuntu_dists_lucid_universe_ binary-i386_Packages*

If you can't run "gksu nautilus" but can use "sudo" in a terminal, try the following.  

Be very careful with the "rm" command. You are running as root and a typo could delete important system files. (That's why tried using "gksu nautilus" first and why we change into the *lists* directory before using the *rm* command.)  Copying the commands is much safer than typing them out.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak && sudo mkdir /etc/apt/sources.list.d.bak && sudo cp -R /etc/apt/sources.list.d/* /etc/apt/sources.list.d.bak
cd /var/lib/apt/lists
sudo rm my.archive.ubuntu.com_ubuntu_dists_lucid_universe_ binary-i386_Packages

``` 

2. To try to correct the error message:
> 
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 8388608.


```
gksu gedit /etc/apt/apt.conf.d/20archive
```
Change the value of > APT::Archives::MaxSize "500"; to a higher value. (Note - your MaxSize number may already be higher than 500. I'd set it to much higher until you get the problem fixed.)

3. If you are unable to use the commands because of the error message, try booting to the recovery mode and select the "root" option.

At the root command prompt, run the following. The first set of commands just backs up your current sources.list and sources.list.d folder. *If you ran this command earlier, it is not necessary to run it again.* The third removes the repository list generating the error. It's possible that it is not just the one causing the problem. We back up the entire lists in case we have to remove all the lists later. 

Be careful with the "rm" command. You are running as root and a typo could delete important system files. (That's why we change into the *lists* directory before using the *rm* command. Use the "reboot" command when you are finished to reboot to your normal system.
```

cp /etc/apt/sources.list /etc/apt/sources.list.bak && mkdir /etc/apt/sources.list.d.bak && cp -R /etc/apt/sources.list.d/* /etc/apt/sources.list.d.bak
cd /var/lib/apt/lists
rm my.archive.ubuntu.com_ubuntu_dists_lucid_universe_ binary-i386_Packages
reboot

```
If you aren't sure of the filename, you can get rid of all the package lists with "rm *Packages". We can restore them later.
See if the problem is solved.
If not:

4. Boot back to recovery mode. Use the *nano* text editor to change the cache limit as mentioned in the error message.
```

cp /etc/apt/apt.conf.d/20archive /etc/apt/apt.conf.d/20archive.bak
nano /etc/apt/apt.conf.d/20archive
```
Change the value of > APT::Archives::MaxSize "500"; to a higher value. (Note - your MaxSize number may already be higher than 500. I'd set it to much higher until you get the problem fixed.)

If you aren't familiar with *nano*, make the change, then CTRL-x, then Y to save.

---

### Post by maizuddin35 on 2010-09-11
thanks for the reply, I wont be using my ubuntu for now, but I will try this later. I hope you guys will be here for this problem, if its occur again.

---

### Post by maizuddin35 on 2010-09-18
It is harder than I taught it was. I need to remove all the package one by one didnt I? I search at the lists of files in the lists folder,and I remove it manually, but when each time I apt-get update , a new package appear with error, so than, I remove it once again, and again and again. Then, I use rm * the packages inside that folder.

after that, I apt-get check , says its done. Then apt-get update && upgrade, the problem once again appear. 

for now, maybe I manage to deal with the package that I can remove, but I have problem increasing the apt cache size.

---

### Post by drs305 on 2010-09-18
> **maizuddin35 said:**
> It is harder than I taught it was. I need to remove all the package one by one didnt I? I search at the lists of files in the lists folder,and I remove it manually, but when each time I apt-get update , a new package appear with error ... 

That method is probably going to take you through hundreds of packages.

Instead, try renaming the repository lists manually. 
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.bad
```
Then try refreshing the repository lists:
```
sudo apt-get update
```
That should clear any "Merge list" error messages.

If you still can't open synaptic, run the command in a terminal and tell us the error message:
```
gksudo synaptic
```

---

### Post by maizuddin35 on 2010-09-19
```
adibmobile@empatbelas:~$ sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory

```

after I mv the lists to lists.bad and apt-get udpate this appear..
have I done something wrong, I didnt open any synaptic or software sources

---

### Post by maizuddin35 on 2010-09-20
can you teach me how to rename it manually ?

---

### Post by maizuddin35 on 2010-09-20
after i have move the lists to lists.bad, i have copy back lists.bad to lists.

then I apt-get update

and here is the end result

```
adibmobile@empatbelas:~$ sudo apt-get update
[sudo] password for adibmobile: 
Get:1 http://my.archive.ubuntu.com lucid Release.gpg [189B]                    
Ign http://my.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release.gpg [198B]   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Get:3 http://archive.ubuntu.com lucid Release.gpg [189B]             
Ign http://my.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Get:4 http://archive.ubuntu.com lucid Release [57.2kB]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Get:5 http://security.ubuntu.com lucid-security Release [38.5kB]
Get:6 http://my.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://my.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://my.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Get:7 http://my.archive.ubuntu.com lucid Release [57.2kB]                      
Get:8 http://archive.ubuntu.com lucid/main Sources [659kB]                     
Get:9 http://security.ubuntu.com lucid-security/main Packages [71.2kB]         
Get:10 http://security.ubuntu.com lucid-security/main Sources [26.4kB]         
Get:11 http://my.archive.ubuntu.com lucid-updates Release [44.7kB]             
Get:12 http://security.ubuntu.com lucid-security/universe Sources [9,415B]     
Get:13 http://security.ubuntu.com lucid-security/universe Packages [36.6kB]    
Get:14 http://my.archive.ubuntu.com lucid/main Packages [1,386kB]              
Ign http://my.archive.ubuntu.com lucid/main Packages                           
Hit http://my.archive.ubuntu.com lucid/main Sources
Hit http://my.archive.ubuntu.com lucid/universe Sources
Hit http://my.archive.ubuntu.com lucid/universe Packages                       
Hit http://my.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://my.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://my.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://my.archive.ubuntu.com lucid-updates/universe Packages               
Ign http://my.archive.ubuntu.com lucid/main Packages                           
Get:15 http://my.archive.ubuntu.com lucid/main Packages [1,781kB]              
66% [15 Packages gzip 0B]                                    1,366B/s 16min 54s
gzip: stdin: not in gzip format
Err http://my.archive.ubuntu.com lucid/main Packages                           
  Sub-process gzip returned an error code (1)
Fetched 1,579kB in 15min 4s (1,746B/s)                                         
W: Failed to fetch http://my.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)

E: Some index files failed to download, they have been ignored, or old ones used instead.
adibmobile@empatbelas:~$ 

```

---

### Post by drs305 on 2010-09-20
Have you tried changing servers via either Synaptic or Software Sources? (Settings, Repositories: Software tab: Download From:)

---

### Post by maizuddin35 on 2010-09-20
thanks for the help drs305, i have now face the same problem again.

okey, yesterday, i already mv the lists to lists.bad, and cp lists.old to lists, and update it, and I update it with the new post yesterday, then you tell me to change the server, so I change it from the Malaysia server to the main server and apt-get update and end up the same problem all over again.. .

---

### Post by maizuddin35 on 2010-09-21
thanks to you guys, for now, I don't have any porblem wehn want to apt-get update,

I use gksu synaptic to open synaptic and change the repository back again, I untick the universe and all the packages .

and after that, I reload, and it all goes fine. No problem or anything for now.

when i apt-get update here is the output 

```
adibmobile@empatbelas:~$ sudo apt-get update
Hit http://archive.ubuntu.com lucid Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Hit http://archive.ubuntu.com lucid Release
Hit http://archive.ubuntu.com lucid-updates Release
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Reading package lists... Done

```

what I can see here, packages update is less than before, what should I do , when I want to keep track with my other packages to update?

---

### Post by drs305 on 2010-09-21
The repositories that you normally would have selected in Synaptic/Software Sources are:

Ubuntu Software tab:
Main
Universe
Restricted
Multiverse

Other Software:
Ubuntu Partner (if desired)
Any third-party repositories you may have manually added.

Updates:
Important security updates
Recommended updates (normally selected)

---

### Post by maizuddin35 on 2010-09-21
I see, thank you very much , I think this thread is solved.i hope my problem will not come back again.

---

