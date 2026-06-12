---
title: "Files permissions/ownership [long and not for the faint of heart]"
date: 2009-08-13
forum: General Help
---

### Post by tgeer43 on 2009-08-13
Hi again all,

First a little background that will hopefully provide some insight.
I had to do a totally unexpected restore of my 9.04 64-bit installation. The system had been rendered unbootable (corrupted MBR and grub) but I was still able to access all of the files. So I booted a copy of Puppy Linux off of a USB flash drive and copied all of the files on the partition to a separate drive using Puppy's ROX file manager. Just for good measure I also tar'd up an archive of all the files to the second HD as well.

I had been wanting to increase the size of my Ubuntu partition but wasn't able to just expand it with gparted and then rewrite the MBR and reinstall grub. That's because I had a bunch of old partitions laying around both before and after my Ubuntu partition and there was no way to merge all of the unallocated space and grow the Ubuntu partition to fill it. So since I had all of my files backed up I deleted all partitions except sda1 which holds a minimal install of Win Vista. That allowed consolidation of all the free space into one big unallocated chunk. I then did a fresh install from the Live CD which set up the main Ubuntu and swap partitions, rewrote the MBR and gave me back a good grub. Then I simply copied all of the backed-up files from the second HD to the new installation. That way I wouldn't have to do any updating, configuring, tweaking, etc. to get my system back exactly as it was prior to the catastrophe. I know that's probably not the 'normal' way to do things but it seemed like a reasonable alternative to spending dozens of hours rebuilding from scratch.

Upon booting the newly restored system, at the login prompt I got an error dialog stating, in part: "User's $HOME/.dmrc file is being ignored... The file should be owned by user and have 644 permissions. User's $HOME directory must be owned by user..."

That was easy enough to track down. I booted into recovery mode and issued the following commands:
```
chmod 644 /home/tgeer/.dmrc
chown tgeer /home/tgeer/.dmrc
chmod 700 -R /home/tgeer
chown -R tgeer /home/tgeer
```Seems like the first two command are overridden by the second two but that's the instructions that I found and they worked. The system then booted normally - or so it seemed. Now to the crux of the problem. It seems there are still some permission/ownership issues and other, possibly related woes. Here's what I have done and observed since doing the above:

    * Sudo commands in the terminal were producing the error: "sudo: must be setuid root". Again I booted into recovery mode and issued the following commands:
    ```
chmod 4755 /usr/bin/sudo
chmod 4755 /bin/su
```Then I started getting this: "sudo: /etc/sudoers is mode 0777. Should be 0440". Back to recovery mode to issue:
    ```
chmod 0440 /etc/sudoers
```This resurrected sudo and I have all superuser priveleges back now.
    
* My command prompt is now: tgeer@localhost instead of: tgeer@tgeer. The system was labeled 'tgeer' at installation time and my username is 'tgeer'. Entering superuser mode with 'sudo -s' gets me: root@localhost BUT my recovery mode prompt is correct: root@tgeer. Hmmm...
    
* No internet connection and no network manager icon/applet in the panel. My connection is normally initiated via /etc/rc.local with the following code:
    ```
ifconfig wlan0 up
iwconfig wlan0 mode managed
iwconfig wlan0 essid  08FX02002785 
iwconfig wlan0 key open XXXXXXXXXX (my WPA key goes here)
dhcpcd -d wlan0
```When I issue these commands manually in the console with sudo, the lines all execute cleanly except the last one which produces this error: "The program dhcpcd is currently not installed. You can install it by typing: apt-get install dhcpcd". But it IS installed and in fact if I boot into recovery mode with networking, DHCPCDiscovery runs and attempts to connect but fails. Besides, how would I apt-get install it without an internet connection anyway?
    
* No sound. Volume control icon in the panel has a red 'X' on it and trying to access it gives the following error: "No volume control GStreamer plugins and/or devices found". Something else that I tried with the sound (might have been alsa-mixer) gave me an error message saying something about the possibility of the sound card not being configured. Just like everything else here, this worked just fine previously and my sound device settings in System->Preferences->Sound all look OK but the test buttons no longer produce a tone.
    
* The preferences for the clock applet in the panel have the option to change the time greyed out. Actually this might be fixed after getting sudo working again. I haven't checked it since then.
    
* When browsing the filesystem with nautilus, I am seeing a number of files and folders with the red 'X' emblem. Not the whole icon, just the red 'X' emblem superimposed in the upper-right of the actual icon. This is supposed to indicate 'unreadable' but the files/folders are indeed readable and if I right-click one of them and choose properties then go to the emblems tab, the unreadable emblem is not selected (nor is any other).

I know it sounds like a huge furball but I have a suspicion that it's all related and still has something to do with permissions/ownerships. I just don't know where to go from here. I'm hoping you folks who have helped me so much in the past will have some ideas. Hell, maybe it's something painfully obvious but not to me. I've only got about one year with Linux under my belt. The only thing I can think of is that copying the files back and forth with Puppy Linux and ROX did not preserve the file permissions and/or ownerships. Maybe I'd have better luck untarring the archived backup back over the top of everything?

Phew - I'm getting cauliflower fingers. :)

Thanks in advance for any ideas or suggestions you may have.

tgeer

---

### Post by jocko on 2009-08-13
My advice: Back up your /home directory and reinstall.
Accept it. It will probably take years to figure out the permissions for every file of the system and get it all right, while it will take 10 minutes to completely reinstall ubuntu, plus whatever time you need to install your applications.

---

### Post by tgeer43 on 2009-08-13
> **jocko said:**
> My advice: Back up your /home directory and reinstall.
Accept it. It will probably take years to figure out the permissions for every file of the system and get it all right, while it will take 10 minutes to completely reinstall ubuntu, plus whatever time you need to install your applications.

Well jocko, you'd be correct in most instances but in this case there's more to it than the 10 minutes it takes to reinstall plus the time needed to reinstall apps. It's more like 60+ hours of configuring, updating, optimizing, cleaning, tweaking, trimming, compiling, lathering, rinsing, and repeating.

You see, I'm one of those super anal-retentive type-A personalities who must hand-massage every single byte of the filesystem until it's just exactly the way that I want it - with emphasis on speed, efficiency and reduced resource usage but without sacrificing functionality or aesthetics. I have this 9.04 64-bit installation screaming along at hyperspeeds and occupying little more than a bit over 2GB of disk space including compiz fusion, flash, java and wine but not including other additional apps and games. That's pretty darn lean and when idling at the desktop it requires less than 256MB of RAM with compiz fusion, an extensive conky, a bucketload of applets running and 4 large, hi-resolution desktop backgrounds plus a skydome. Not too shabby, especially considering that 64-bit does require a bit more memory than an equivalent 32-bit installation. This was done primarily by very careful management of loaded and running processes (only about 160 loaded compared to a bit over 200 for a typical installation) and again without any loss of functionality or aethetics. In fact I'm loaded for bear when it comes to desktop effects and other eye-candy. I mean what's the sense in running Ubuntu at all unless I can show it off and make Windows look like the garbage heap that it really is. Otherwise I might as well run one of the minimalist distros like DSL or Puppy.

So as you can see, this is about as far from a 'typical' installation as you can get and I think it deserves a bit of resuscitative effort before giving it up for dead. Once I'm completely finished (and I was about 95% there), it's my intention to clone the installation to a fast USB flash drive for portability and rescue/maintenance operations. It sure beats the heck out of using the slow booting, slow running Live CD. I'll only need a 4GB stick since I won't be including any games or other trivial apps in the USB flash install. Sure, there will be lots of rescue and maintenance oriented apps on it but they usually have relatively modest disk space requirements. Nowadays you can pick up a fast 4GB USB thumbdrive for the price of a few packs of cigarettes.

And one of these days I'll even get around to documenting all of the steps to get from the initial install to to where I'm at - not only in case I do have to rebuild from scratch in the future but also for the possible benefit of others who may want a fast and compact yet attractive and highly functional Ubuntu installation.

But, if it does turn out that all or most of the file permissions and/or ownerships are well and truly screwed up then yes, I'll probably have no choice but to start from scratch again. But despite the evidence, I'm not fully convinced that things are that hopeless. In fact I think that I'm just about there in getting things straightened back out. The main thing was sudo and that's already fixed. Next priority is internet connectivity.

So let me ask you and the others a couple of things:

* What do you make of the fact that my command prompt lists the machine name as localhost instead of what I assigned to it during the installation? Remember too that if I boot into recovery mode it shows the correct machine name.

* I'm thinking that using ROX-filer and Puppy Linux to copy the backed-up files back over to the new installation was a mistake and may be the source of most or all of my troubles. Does anyone know definitively what happens to the file permissions and ownerships when using ROX-filer like this? Do you think I'll have different/better results by untarring the gzipped archive that I made of the entire system? The more I think about it the more I like the idea because then I can use the '--preserve-permissions' and '--same-owner' options which theoretically should preclude any permission/ownership issues. I'm going to try it at any rate but would still like to hear anyone's input on this. I probably should have done that right from the get-go and maybe I wouldn't be writing this right now but what can I say? I'm a dumba$$ ex-Windows user who is much too used to doing almost everything in a nice comfy GUI environment. It's been a long, long time since my UNIX and Apple DOS days and I need to get reacquainted with doing things at the command line, especially if I'm going to continue doing all of these esoteric things.

* Any idea why when I issue a dhcpcd command I'm told that the program is not installed when it actually is? I guess I could reinstall it if I can find a .deb package since I can't apt-get it without an internet connection. This is almost certainly the (only) reason that I have no internet connectivity since the rest of my wlan0 startup commands in rc.local execute without error.

* And lastly, what do you think about the files and folders that I see in nautilus with the 'unreadable' emblem on the icon when the files/folders are all actually quite readable and don't seem to be affecting things negatively?

Well, this started out to be a short reply - so much for that. I wouldn't blame anyone who didn't want to wade through all of my delirious ramblings. I'm now on day 5 of no sleep whatsoever (I'm a wicked bad insomniac) and I'm so cranked up that I don't feel like I'll ever sleep again - or at least not until my system is back up and running normally. :-?

tgeer

---

### Post by jtp755 on 2009-08-13
If your users and system name are the same and you said you created a tarball of all the files why not use -P with tar so that it keeps the permissions on extraction?

---

### Post by tgeer43 on 2009-08-13
> **jtp755 said:**
> If your users and system name are the same and you said you created a tarball of all the files why not use -P with tar so that it keeps the permissions on extraction?Yeah, jt - thanks. That's just what I was asking/talking about right here:
> **tgeer43 said:**
> Do you think I'll have different/better results by untarring the gzipped archive that I made of the entire system? The more I think about it the more I like the idea because then I can use the '--preserve-permissions' and '--same-owner' options which theoretically should preclude any permission/ownership issues. I'm going to try it at any rate but would still like to hear anyone's input on this.If you missed it, I can't blame you. It's buried pretty deep in my last epic diatribe. :wink:

It may seem like an obvious no-brainer but I've no real world experience with restoring a system from a tarball. I mean, I know the tar command well enough but I'm not familiar with the effects and possible ramifications of untarring an entire installation to a boot partition like that. The many articles on the internet about using 'tar' to back up and restore don't ever mention anything about using any special options with tar. This would almost certainly cure the permission, ownership, and sudo issues that I had to correct manually but I don't know about the other issues such as no internet, no sound, the mysterious 'unreadable' emblems on some of the files and folders, and the fact that my system name in the console is listed as 'localhost' instead of 'tgeer' unless I'm at a recovery mode command prompt. I suppose that these too could be permission/owner/sudo related but unless someone chimes in I'll not know until I just do it.

I guess I'll find out soon enough. I'll post back and let y'all know how it went.

Thanks,

tgeer

Oh yeah, FWIW the short form of the --preserve-permissions option is -p rather than -P, which is short for --absolute-paths.

---

### Post by tgeer43 on 2009-08-20
Well, my computer made the decision for me. Massive numbers of bad blocks on my primary drive forced me to buy a new one and I decided to get a fresh start by reinstalling and copying over my /home directory.

tgeer

---

