---
title: "Flash movies don't play."
date: 2009-08-10
forum: General Help
---

### Post by cycrosism on 2009-08-10
I was trying to play this game on facebook called "FarmVille"

Here is the link to it: [http://apps.facebook.com/onthefarm/index.php?ref=bookmark](http://apps.facebook.com/onthefarm/index.php?ref=bookmark)

and it just starts to load and as it does it just loads 1 bar and doesn't move no matter how long I wait. I installed Adobe and Macromedia Flash player and they didn't help so I uninstalled them both and they didn't do anything different.

I am not sure what to do at this point, as I have tried so much stuff and I was just wondering if I could get help from you guys.

I am using firefox by the way.

Edit - This isn't just this game, its all flash things although youtube works kind of good.

---

### Post by Soul-Sing on 2009-08-10
How did you install (adobe) flash(nonfree)?
Thats the key question. 
Problems with playing youtube also? Or only this feature wthin facebook?

---

### Post by cycrosism on 2009-08-10
Yeah I did is there something wrong with that program?

Youtube video's play up too.

---

### Post by WatchingThePain on 2009-08-10
I have Jaunty 64bit and also Farmville does not work (grey box on screen).
Generally all other flash stuff works since I installed ubuntu restricted extras. I don't think its a flash problem on mine. If Farmville has some kind of adware then maybe it's being blocked.

Also for those not familiar with farmville..I'd say it's a bit similar to Second Life.  Would I be dumb therefore to guess that Farmville installs a server client on your machine and so theres security issue?.

I suspect that but I don't know.

---

### Post by cycrosism on 2009-08-10
Well the FarmVille application loads, but once it appears and says "Loading" and has a progress bar on the application itself that bar just stays at 0% and doesn't move

---

### Post by WatchingThePain on 2009-08-10
Yes I got that at first it looked like it was going to work but then the big grey box that just stays there.
Really Facebook should have an answer to this but believe me, they are hard as hell to contact.
I also wonder if it's a compatibility issue with my OS.

I haven't tried this yet but what about opening it using a different browser, like Chrome or something?.

---

### Post by cycrosism on 2009-08-10
Yeah I had a thread on this before but I didn't get the answer I wanted

[http://ubuntuforums.org/showthread.php?p=7720352#post7720352](http://ubuntuforums.org/showthread.php?p=7720352#post7720352)

I have tried so many things but still the videos are bad

---

### Post by Soley on 2009-08-10
I had that issue the other day. I rebooted & haven't had it since. Every video I tried to watch would play for like 4 seconds then stop.

---

### Post by cycrosism on 2009-08-10
When I am watching a YouTube video, if I move my mouse while the video is playing it lags A LOT. I installed the Ubuntu Restricted Extra's and it still won't work good :(

---

### Post by cycrosism on 2009-08-10
My graphics card is the Nvidia 9800GT 512MB. My drivers are the default

"NVIDIA accelerated graphics driver (version 180) [Recommended]"

Does that have something to do with it?

---

### Post by cycrosism on 2009-08-10
Hi, could anyone please help me with this situation?

---

### Post by WatchingThePain on 2009-08-10
> **cycrosism said:**
> My graphics card is the Nvidia 9800GT 512MB. My drivers are the default

"NVIDIA accelerated graphics driver (version 180) [Recommended]"

Does that have something to do with it?

I wouldn't have thought so. That's a pretty decent card. I use nvidia geforce and as I say all my Flash works, youtube works perfect. It's just Farmville doesn't work.

---

### Post by cycrosism on 2009-08-10
Well I just did some checking around and I see that FarmVille is a swf?

The funny thing is that it loads the application and I can see the loading screen of the swf application but it wont load any further after that

---

### Post by WatchingThePain on 2009-08-10
> **cycrosism said:**
> Well I just did some checking around and I see that FarmVille is a swf?

The funny thing is that it loads the application and I can see the loading screen of the swf application but it wont load any further after that

SWF just means shockwave flash.
I think maybe the first thing to try is a different browser but one of the newer ones.

---

### Post by funky_D on 2009-08-10
i'm having flash problems too since the last update, (last week).
before it was OK, but the update said to install flashplayer...
any way to show what is installed so anyone can help?

Thank you
Dino (kubuntu 9.04 - 2.6.27-14-generic)

---

### Post by JavaBeanHead on 2009-08-10
Give this a try and report back . . . it worked for me (as I was experiencing similar problems).  Open Syntaptic Package Manager and in the quick search toolbar at the top type gstreamer . . . 

After the results have populated, scroll down to near the bottom of the list, and mark for installation the entry titled "ubuntu-restricted-extras", and apply it.  

I don't know if a restart is necessary, but I did it just to be sure it solidified the changes.  

Works like a charm.  I'll credit "Ubuntu Kung Fu: Tips, Tricks, Hints, and Hacks" by Keir Thomas for this little tidbit.  If it doesn't work for you, sorry about that - but I still think this book is a gem.

---

### Post by zkriesse on 2009-08-10
Go to this page and download the .deb file for Ubuntu 8.04+. [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) Make sure you save it to the desktop. After you do that either double click on the file which should be on your desktop or run this command in the terminal.

sudo dpkg -i install_flash_player_10_linux.deb

Follow the instructions the installer gives you...let me know how it turns out.

---

### Post by denfoote on 2009-08-11
> **Zachk18 said:**
> Go to this page and download the .deb file for Ubuntu 8.04+. [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) Make sure you save it to the desktop. After you do that either double click on the file which should be on your desktop or run this command in the terminal.

sudo dpkg -i install_flash_player_10_linux.deb

Follow the instructions the installer gives you...let me know how it turns out.

enfoote@denfoote-desktop:~$ sudo dpkg -i install_flash_player_10_linux.deb
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
denfoote@denfoote-desktop:~$

---

### Post by funky_D on 2009-08-11
i did the:

sudo dpkg -i install_flash_player_10_linux.deb                        
                                                   
Selecting previously deselected package adobe-flashplugin.                                              
(Reading database ... 132595 files and directories currently installed.)                                
Unpacking adobe-flashplugin (from install_flash_player_10_linux.deb) ...                                
dpkg: dependency problems prevent configuration of adobe-flashplugin:                                   
 adobe-flashplugin depends on libnspr4-dev; however:                                                    
  Package libnspr4-dev is not installed.                                                                
 adobe-flashplugin depends on libnss3-dev; however:                                                     
  Package libnss3-dev is not installed.                                                                 
dpkg: error processing adobe-flashplugin (--install):                                                   
 dependency problems - leaving nconfigured                                                             
Errors were encountered while processing:                                                               
 adobe-flashplugin                                                                                      

droliveira@metalgear:~/Downloads$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libnspr4-dev libnss3-dev
The following NEW packages will be installed:
  libnspr4-dev libnss3-dev
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 519kB of archives.
After this operation, 2904kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libnspr4-dev 4.7.5-0ubuntu0.9.04.1 [263kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main libnss3-dev 3.12.3.1-0ubuntu0.9.04.1 [255kB]
Fetched 519kB in 0s (1117kB/s)
Selecting previously deselected package libnspr4-dev.

I didn't even did dpkg to the deb again and flash is working again, i think in the last ubuntu update they removed this librarys. Now it's working!
Thank you for your help! =)

Dino

---

### Post by denfoote on 2009-08-11
Did all of the above and flash still does not work!!

None of my flash content works.

Hulu, news feeds, nothing!!

I need ideas.

---

### Post by funky_D on 2009-08-12
> **denfoote said:**
> Did all of the above and flash still does not work!!

None of my flash content works.

Hulu, news feeds, nothing!!

I need ideas.

it may sound silly but did you get the packet from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) ? then do the dpkg to it because in your previous post you do not seem to have the packet or to be doing dpkg on the wrong directory of the packet

---

### Post by cycrosism on 2009-08-13
Okay - I have tried all of this and it still wont work fine

---

### Post by JayKay3000 on 2009-08-13
erm. I assume you have flash enabled in the browser?

But as long as you have all the right codecs installed flash,etc theres no logical reason why it should not work.

I've just tried this application and it seems to work fine in firefox. Though I've only loaded it to the setup screen. Check the add-ons tab to see what is installed under plugins. (Tools, add-ons, plugins)

---

### Post by baddison_uk on 2009-08-13
I've been hacking for weeks trying to get a version of Flash that the Oracle Metalink site will accept - in the end it all came down to swfdec - once I removed that, yeehah!!:)
 
Try getting shot of swfdec:
System/SynapticPackageManager and completely remove swfdec-mozilla.
 
HTH........

---

### Post by ElLute on 2009-09-30
> **baddison_uk said:**
> Try getting shot of swfdec:
System/SynapticPackageManager and completely remove swfdec-mozilla.


I purged swfdec-gnome to make working FV on FB...

incredible :)

---

