---
title: "how can i just erase a gnome package that refuses to update?"
date: 2009-10-22
forum: General Help
---

### Post by loom232 on 2009-10-22
I have 1 update that will not update and I can't seem to just erase the package. It is the Gnome games data package which is apparently badly corrupted. I don't need this program and wouldbe happy just to see it gone.

I have tried many different sudo commands ..but the same problem remains.

I have tried repairing the 'broken pakage' ...no success.

Because I can't resolve this problem I am unable to install or uninstall any programs using Add/Remove



Can I just access a program file repository somewhere and just delet the offending package?




Any help would be appreciated

---

### Post by QLee on 2009-10-22
[QUOTE=loom232]
Any help would be appreciated[/QUOTE]

You are going to get more useful answers if you show the exact error message you see and detail what commands you tried (and what errors they dropped), rather than asking a general question like you did and saying you tried many commands.

[QUOTE=loom232]
Can I just access a program file repository somewhere and just delet the offending package?[/QUOTE]

No. You will want to fix the broken package so your package management system can function again. Someone will be able to help you do that after you give more complete information.

---

### Post by drs305 on 2009-10-22
QLee is correct. We can help but need to no the exact error messages. APT does a great job of keeping track of packages and their status, but it can become corrupted by randomly deleting files. 

Your problem could be a variety of things and the solutions can vary widely. If necessary, we can go in and alter the APT 'database' files but this should be done only after we try to do what APT tells us to do.

Run the following commands and post the error message(s). If there is another command that consistently produces an error post that one as well.

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by loom232 on 2009-10-22
Hi thanks very much for the reply . I ran the two commands you mentioned update and upgrade

the result was

michael@TOSHIBA-User:~$ sudo apt-get update
[sudo] password for michael: 
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy Release.gpg                                                          
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/main Translation-en_US                                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona Release.gpg
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy Release       
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy Release.gpg                   
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/multiverse Translation-en_US  
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona Release            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                                    
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/main Packages 
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/universe Packages
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/multiverse Packages
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/restricted Packages
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/universe Translation-en_US
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/main Translation-en_US
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/restricted Translation-en_US
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy Release  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages           
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/main Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/universe Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/multiverse Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/restricted Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public Packages
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public Sources
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/multiverse Packages
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/universe Packages
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/main Packages
Ign [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/restricted Packages
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/multiverse Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/universe Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/main Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/restricted Sources
Err [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/multiverse Packages
  404 Not Found
Err [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/universe Packages
  404 Not Found
Err [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/main Packages
  404 Not Found
Err [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/restricted Packages
  404 Not Found
W: Failed to fetch [http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://ubuntu.qatar.cmu.edu/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
michael@TOSHIBA-User:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-games-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/14.6MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 87604 files and directories currently installed.)
Preparing to replace gnome-games-data 1:2.22.3-0ubuntu2netbook4 (using .../gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb) ...
Warning: /usr/share/gconf/schemas/blackjack.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotski.schemas could not be found.
Warning: /usr/share/gconf/schemas/mahjongg.schemas could not be found.
Warning: /usr/share/gconf/schemas/glchess.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnomine.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnobots2.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnect.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotravex.schemas could not be found.
Warning: /usr/share/gconf/schemas/iagno.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnibbles.schemas could not be found.
Warning: /usr/share/gconf/schemas/gtali.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnometris.schemas could not be found.
Warning: /usr/share/gconf/schemas/same-gnome.schemas could not be found.
Warning: /usr/share/gconf/schemas/glines.schemas could not be found.
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
WARNING: /usr/share/python-support/gnome-games-data does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/gnome-games-data does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@TOSHIBA-User:~$ 

I really appreciate your help with this

regards

mike

---

### Post by drs305 on 2009-10-22
First, let's clean up the archives repository. It will remove the archives, which you don't need once a package is installed.
```

sudo apt-get clean

```
Getting rid of the bad package in the archives section may not be enough, but it will be the easiest thing to do as a first step.

We can also clean up your sources.list if you have been getting that update error for a while.  Go into Synaptic > Settings > Repositories. If qatar is your default repository, replace it with another one. Download from > select Other and either Choose Best Server or pick one close to where you live. Hit Reload when you are done. If it is just an added repository, untick it in the Third Party tab.

---

### Post by loom232 on 2009-10-22
Thank you very much for your reply.

I did as you said and ran sudo apt-get clean. typed my password and nothing happened. (did it 3 times ..nothing!)

Then unclicked the Qatar repository from the 3rd party tab in synaptic.

I now have two updates that won't update Gnome games data and now Firefox 2

Ithen tried to run Add / Remove and got a warning ..

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I performed bot of these commands and got

michael@TOSHIBA-User:~$ sudo apt-get update
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy Release.gpg
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona Release.gpg
Ign [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                     
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy Release                      
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona Release                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                                                   
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/main Packages                
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/universe Packages
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/multiverse Packages
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/restricted Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                           
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/main Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/universe Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/multiverse Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy/restricted Sources
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public Packages
Hit [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy Release.gpg
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy Release
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/multiverse Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/universe Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/main Sources
Hit [http://ubuntu.qatar.cmu.edu](http://ubuntu.qatar.cmu.edu) hardy/restricted Sources
Reading package lists... Done
michael@TOSHIBA-User:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gnome-cards-data libgtksourceview1.0-0 libnm-util0 libggzmod4 libclutter-0.6-0 guile-1.6-libs dhcdbd python-bittorrent
  libggz2 libgtksourceview-common libqthreads-12 gnome-games-data libggzcore9 libisc32 python-gnome2-desktop
  libguile-ltdl-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-2 gnome-games-data
Suggested packages:
  firefox-2-gnome-support latex-xft-fonts
Recommended packages:
  gnome-games gnome-games-extra-data
The following packages will be upgraded:
  firefox-2 gnome-games-data
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 23.7MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public gnome-games-data 1:2.22.3-0ubuntu2netbook5 [14.6MB]
Get:2 [http://toshiba-arizona.archive.canonical.com](http://toshiba-arizona.archive.canonical.com) hardy-toshiba-arizona/public firefox-2 2.0.0.19+nobinonly1-0ubuntu0.8.04.1 [9069kB]
Fetched 23.7MB in 4min11s (94.2kB/s)                                                                                        
(Reading database ... 87604 files and directories currently installed.)
Preparing to replace gnome-games-data 1:2.22.3-0ubuntu2netbook4 (using .../gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb) ...
Warning: /usr/share/gconf/schemas/blackjack.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotski.schemas could not be found.
Warning: /usr/share/gconf/schemas/mahjongg.schemas could not be found.
Warning: /usr/share/gconf/schemas/glchess.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnomine.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnobots2.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnect.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnotravex.schemas could not be found.
Warning: /usr/share/gconf/schemas/iagno.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnibbles.schemas could not be found.
Warning: /usr/share/gconf/schemas/gtali.schemas could not be found.
Warning: /usr/share/gconf/schemas/gnometris.schemas could not be found.
Warning: /usr/share/gconf/schemas/same-gnome.schemas could not be found.
Warning: /usr/share/gconf/schemas/glines.schemas could not be found.
Warning: /usr/share/gconf/schemas/aisleriot.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
WARNING: /usr/share/python-support/gnome-games-data does not exist.
         Some bytecompiled files may be left behind.
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 269, in <module>
    args.remove(arg)
ValueError: list.remove(x): x not in list
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/gnome-games-data does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Preparing to replace firefox-2 2.0.0.19+nobinonly1-0ubuntu0.8.04.1 (using .../firefox-2_2.0.0.19+nobinonly1-0ubuntu0.8.04.1_lpia.deb) ...
Unpacking replacement firefox-2 ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games-data_1%3a2.22.3-0ubuntu2netbook5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@TOSHIBA-User:~$ 

That's alot of text for a new user...am i getting closer to resolution?

Thankyou

mike

---

### Post by drs305 on 2009-10-22
When you run a command and don't see anything in the terminal thereafter that is a good thing! Ubuntu/Linux only complains when something goes wrong, and then it tries to tell you what it was and sometimes how to fix it. So if you type a command, you often times *want* to see nothing afterward.


Also, when posting large amount of output the preferred practice is to put it between code tags like this [noparse]```
  
```[/noparse]. The easy way is to click on the # symbol in the menu bar of the post window - it will insert the tags and you just paste between them.


Before continuing, you said you tried a lot of stuff. Was one of them trying to fix the broken packages in Synaptic. Open it, on the left side select Custom Filters, Broken Packages. See if the games package is listed and try to fix it. Select it, then Edit, Fix Broken packages. If it seems to work, hit Reload. If not, then >>>


APT is still complaining about the postremoval script. Since your /var/apt/cache/archives file should now be empty, we'll try the next step - removing the bad removal script: We won't delete it, we will just move it where APT won't look for it.

```

sudo mv /var/lib/dpkg/info/gnome-games-data* ~/Desktop 

```.
This moves the gnome-games-data install records (including the post-removal script) to your Desktop. When you enter the command you won't see anything happen.

Then try this one again:
```

sudo apt-get upgrade

```

If it still complains, we'll move on to the next step.

---

### Post by loom232 on 2009-10-23
Success!!! I appear to be back up and runnng. No more warnings , no more 'upgrades available' that won't upgrade...my add / remove is back in working order..

Thank you very much indeed for your help and support (and patience). I really appreciate it.

Regards

Mike

---

### Post by drs305 on 2009-10-23
> **loom232 said:**
> Success!!! I appear to be back up and runnng. No more warnings , no more 'upgrades available' that won't upgrade...my add / remove is back in working order..

:P  Just a clean up item. We moved some system files to your Desktop. You cannot delete them as a normal user - only root can do that. And when you delete something as root it goes to root's trash bin, not yours. That means a you as a normal user can't remove the files by emptying your Trash Bin, and they will continue to take up space.

To delete them, a safe way is to open a file browser as root:
```
gksu nautilus ~/Desktop
```
It should open and you should see the games-data files. If you use SHIFT-DEL to remove them, they will bypass the Trash and be gone forever. (But also be careful not to delete the wrong files, since they would be gone as well.).  And while you have a root browser open, now might be a good time to see if you have much in your root trash bin. CTRL-H to view hidden files. Go to /root/.local/share/Trash and look into the "files" folder. If there are files inside, use SHIFT-DEL to remove them. Same with anything inside the "info" folder. 

*Finally, please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

