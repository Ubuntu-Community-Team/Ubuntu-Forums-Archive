---
title: "Installing Real Player 10 Gold The Right Way"
date: 2006-01-29
forum: General Help
---

### Post by TechSonic on 2006-01-29
RealPlayer acts differently then from Helix Player.  Lot of you may know RealPlayer is developed off the Helix Player Source, but that doesn't mean you're RAM format music will play in it.

Because the Wiki is outdated on this, I've found a solution. Some of it is still good, some....


Follow these Instructions...

First go to [http://www.real.com/](http://www.real.com/) and Download RealPlayer 10 Gold
You should get an file with the extention .BIN

Don't forget to type in the full directory path to where you stored the file you just downloaded.

```
sudo chmod +x filename.bin
```

```
sudo filename.bin
```

During the install it will ask you where you want to store the files.  Instead of installing to you're home directory, use this one instead.

> /opt/RealPlayer

Do not use any other directory but that!  If you use another one, sometimes the link in the Sound and Video menu wont launch RealPlayer, or even show the icon image.

Follow the rest of it's instructions and You're good to go.  Although it does ask you a few more questions, normally you can just skip them, just press enter/return key if you don't understand it.

Now RealPlayer 10 Gold is Installed correctly and you have the newest version.

Go play some .Ram files.

---

### Post by dcstar on 2006-01-29
[QUOTE=TechSonic]RealPlayer acts differently then from Helix Player.  Lot of you may know RealPlayer is developed off the Helix Player Source, but that doesn't mean you're RAM format music will play in it.

Because the Wiki is outdated on this, I've found a solution. Some of it is still good, some....
......[/QUOTE]
Personally, I just have this repository in my /etc/apt/sources.list:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

Then select "realplay" in Synaptic, and install it.

I then have Realplayer 10 installed with all the plugins in the right place for Firefox to work.

---

### Post by TechSonic on 2006-01-29
[QUOTE=dcstar]Personally, I just have this repository in my /etc/apt/sources.list:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

Then select "realplay" in Synaptic, and install it.

I then have Realplayer 10 installed with all the plugins in the right place for Firefox to work.[/QUOTE]


Yeah thats also another way to do it.  Good info there!  Although I've had a bit of trouble with repository downloads for realplayer not installing because of damaged packages.  If it works for you, go for it. I even tried that repository though, sadly it denied me the good files, "uncurrupt".  I would say 0.2% of the additions of repositories I make come out bad.

---

### Post by geek.de.nz on 2006-01-30
:cool:Well, I tried both of the above with no success. 

First I downloaded and installed with 
:KS#apt-get install realplay #(with the above repository set in /etc/apt/sources.list)
and then the other way with the .bin file from realplay.com. Both times the program would start up but not play the .ram files properly. I get no video, but audio on this .ram file (
[http://tagesschau.de/styles/container/video/style_video_real_smil_cover/0,1316,OID5189324_RESreal120,00.ram]("http://tagesschau.de/styles/container/video/style_video_real_smil_cover/0,1316,OID5189324_RESreal120,00.ram")
). Also, realplayer does not start as a plugin for firefox as stated above. Instead mplayer starts and gives no video output as well.

Mplayer in general works :-k, plays MPEGs and other video files (even avi-divx), but no live streams. I installed as stated on [http://ubuntuguide.org/#codecs]("http://ubuntuguide.org/#codecs") (used the repositories like stated on that site but altered for breezy in sources.list)

Anyone can help, PLEASE?

---

### Post by TechSonic on 2006-02-08
Well the install tutorial I posted should of worked, unless you have an unsupported sound card that does not use ESD, OSS, ALSA together.

Could be one of those sound cards where you get only one channel.

Click on the first link in my signature if you have a Sound Blaster card, it could tell you a bit more.  Same info there goes for SB Audigy 2 and up.

---

### Post by callmeray on 2006-02-11
Well I got the realplayer 10 installer from Real today and it won't run because it's looking for some old libraries. SO hell instead of DLL hell I guess.

---

### Post by chrismol on 2006-02-11
When I try to execute the RM .bin file, I get this error:

> error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Any suggestions on how to fix?

---

### Post by geek.de.nz on 2006-02-11
> When I try to execute the RM .bin file, I get this error:

     [quote]
 error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory 
                    
 
Any suggestions on how to fix?[/quote] 
try installing libstdc++ with apt-get:
#sudo apt-get install libstdc++
If that doesn't work try searching for libstdc++ with apt-cache:
#sudo apt-cache search libstdc++
and install the package with spt-get like above with the appropriate package name. Tell me if Real-Player works then because it did not for me. It does not display the video but plays the audio.

---

### Post by dcstar on 2006-02-11
[QUOTE=geek.de.nz]
.......
Also, realplayer does not start as a plugin for firefox as stated above. Instead mplayer starts and gives no video output as well.
.......[/QUOTE]
Do you run "standard" Firefox 1.0.7 or a new version installed into a specific directory?

If FF is not installed in the default directory the package assumes it will be in, the plugins will not be installed in the right place.

Find where your new FF "plugins" directory is, then copy (or link) the nphelix.so and nphelix.xpt files from /usr/lib/mozilla/plugins to that location.

---

### Post by geek.de.nz on 2006-02-11
>  Do you run "standard" Firefox 1.0.7 or a new version installed into a specific directory?
 
If FF is not installed in the default directory the package assumes it will be in, the plugins will not be installed in the right place.
 
Find where your new FF "plugins" directory is, then copy (or link) the nphelix.so and nphelix.xpt files from /usr/lib/mozilla/plugins to that location. 
I got FF 1.0.7 (the standard of ubuntu) installed with apt-get. So this is probably not the problem. 

There are other plugins in /usr/lib/mozilla/plugins (l /usr/lib/mozilla/plugins gives):
flashplayer.xpt    
mplayerplug-in-gmp.so   
mplayerplug-in-qt.xpt  
mplayerplug-in.so       
mplayerplug-in.xpt  
nppdf.so@
libflashplayer.so  
mplayerplug-in-gmp.xpt  
mplayerplug-in-rm.so   
mplayerplug-in-wmp.so   
nphelix.so
libnullplugin.so   
mplayerplug-in-qt.so    
mplayerplug-in-rm.xpt  
mplayerplug-in-wmp.xpt  
nphelix.xpt

The main problem is that Realplayer doesn't even show the video. Please! I still need help on that!

---

### Post by dcstar on 2006-02-11
[QUOTE=geek.de.nz]I got FF 1.0.7 (the standard of ubuntu) installed with apt-get. So this is probably not the problem. 
.......
The main problem is that Realplayer doesn't even show the video. Please! I still need help on that![/QUOTE]
Try a complete removal of Realplayer, and then install the helix-player package in Synaptic and see if that works.

---

### Post by dcstar on 2006-02-11
[QUOTE=geek.de.nz]try installing libstdc++ with apt-get:
#sudo apt-get install libstdc++
If that doesn't work try searching for libstdc++ with apt-cache:
#sudo apt-cache search libstdc++
and install the package with spt-get like above with the appropriate package name. Tell me if Real-Player works then because it did not for me. It does not display the video but plays the audio.[/QUOTE]
libstd++5

Use Synaptic instead of guessing what package you need.

---

### Post by geek.de.nz on 2006-02-11
>  Try a complete removal of Realplayer, and then install the helix-player package in Synaptic and see if that works. 
Yeah I did that but helix-player did not play the desired file. Anyway, I did the following:
#sudo apt-get remove realplay
#sudo apt-get install helix-player
After helix-player didn't play the desired file I just did:
#sudo apt-get remove helix-player
#sudo apt-get install realplay
and removed the other plugins from the /usr/lib/mozilla/plugins directory:
#sudo mkdir /usr/lib/mozilla/plugins/bak
#sudo mv /usr/lib/mozilla/plugins/mplayer* /usr/lib/mozilla/plugins/bak/
and it worked! Woohoo! Now it plays the desired file with video even in the browser window! Hope this helps anyone who runs into the same problem.:D

---

### Post by chrismol on 2006-02-11
Ok, thanks geek.de, I got the lib installed and then the RM .bin file installed ok. But when I try and stream .rm files (pbs.org/frontline), I get this error message:

> could not find an appropriate hxplay or realplay in the system path to use as an embedded player

any more advice?

---

### Post by Alapelli on 2006-02-12
tried the installation as suggested on this tread, eveything wen't well until, I tried to
create the directory : /opt/RealPlayer .  Got the following reply

Copying RealPlayer files...Error creating directory  /opt/RealPlayer (No such file or directory), exiting...
Cleaning up installation files...
Done.

 Note: couldn't create it separately.  Had to go with Home/alapelli....
 But would like to do it that way cause, I like the idea of a separate 
 directory ???

---

### Post by Alapelli on 2006-02-12
Retried a 2nd time but took note of all the scripts. They are as follows:

alan@ubuntu:~$ sudo chmod +x /home/alain/Desktop/RealPlayer10GOLD.bin

alan@ubuntu:~$ sudo /home/alan/Desktop/RealPlayer10GOLD.bin
Extracting files for RealPlayer installation........................

Welcome to the RealPlayer (10.0.6.776) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/alan/RealPlayer]:  /opt/RealPlayer

Copying RealPlayer files...Error creating directory  /opt/RealPlayer (No such file or directory), exiting...
Cleaning up installation files...
Done.

Question ? Do I have to install it in [/home/alan/RealPlayer] ?
How do I correct the error regarding /opt/RealPlayer (No such file or directory)

---

### Post by dcstar on 2006-02-13
[QUOTE=Alapelli]
.......
Question ? Do I have to install it in [/home/alan/RealPlayer] ?
How do I correct the error regarding /opt/RealPlayer (No such file or directory)[/QUOTE]
Try:

sudo mkdir /opt/RealPlayer
sudo chown <your user name> /opt/RealPlayer
your-install-realplayer-blah-blah-blah
chown root /opt/RealPlayer

OR add this to your sources.list and save all the mucking around by installing it via Synaptic:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by Alapelli on 2006-02-13
Big Thanks DC Star,  my first installation via Terminal now completed and  
  working  \\:D/

---

### Post by carverj on 2006-02-15
Yes, hi fellas. I'm having a similar problem. The plug-ins seem to be in the right place, assuming I didnt need to find any extra plugins for this to work and am getting error messages whenever I try to open files.

video/X-RN-MP4 component missing
application/x-pn-imagemap component missing

---

### Post by urbandryad on 2006-05-03
this resources list you guys are posting doesn't appear to exist. Do you have the updated resource URL? :( I'm sad. I want my RealPlayer. ;_;

---

