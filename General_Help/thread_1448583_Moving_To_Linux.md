---
title: "Moving To Linux"
date: 2010-04-06
forum: General Help
---

### Post by khat17 on 2010-04-06
Hi all. Fist thanks for having the forums up to help all newcomers. Next is that I was introduced to PC's on DOS (though first computer experience was a MAC) so the CLI in Linux isn't so strange to me - just learning the new commands to do what I needs to do.

Anyways, I've been wanting to switch for some time now and finally had the courage to do so. To make my life a bit easier I've been using the GUI primarily and trying to make it as friendly as I can, but there are some issues that I have and some applications in Windows that I was wondering if there is something similar on Linux that I could use.

_**SIMILAR APPS**_
The programs that I want to know if there are similar apps to would be these:

[EVERYTHING]("http://www.voidtools.com/")
[WINDIRSTAT]("http://windirstat.info/")
[EXACTFILE]("http://www.exactfile.com/")
[Large Software Password Manager]("http://www.largesoftware.com/html/passwordmanager.html")

I know that there are CLI checksum apps and one GUI that I've seen, but the functionality is somewhat lacking in comparison.

SKYPE on Linux has much less functionality than the one for Windows, and I haven't been able to find a third-party application to replace that.

I believe there are some applications that will record your passwords and such, but I'm looking for a central application that will auto-fill the fields in my browser similar to LSPM. I purchased that but the updates are few and far between, and there's no Linux version. Still it's a nice app......

_**PROBLEMS**_
I've noticed that two of my partitions will not mount occasionally and I had to use MOUNT MANAGER to set the mount points myself. 

I realized that occasionally with 9.x external media would not auto-mount and I would have to mount them myself........not sure why though.

Below is a copy of the settings applied by MOUNT MANAGER.

> 
/dev/fd0    /media/floppy0    vfat    noauto    0    0
UUID=A834055834052AC0    /media/PRIMARY    ntfs-3g    defaults    0    0
UUID=F08A8AA68A8A68C4    /media/MUSIC    ntfs-3g    defaults    0    0
UUID=90D4501CD45006BE    /media/STEAM    ntfs-3g    defaults    0    0
UUID=9CB85196B851702E    /media/BACKUP_TEMP    ntfs-3g    defaults    0    0
UUID=94E0D21AE0D20302    /media/TEMP1    ntfs-3g    defaults    0    0
UUID=02C80807C807F825    /media/TEMP2    ntfs-3g    defaults    0    0
UUID=5fa0e8c4-63c9-452d-ac6b-ed26c8794570    swap    swap    sw    0    0
UUID=a0a8b63e-992c-4225-9320-fb1150c9ec33    /    ext4    defaults    0    1
UUID=01C98F0124170F00    /media/DOCUMENTS    ntfs-3g    defaults    0    0
UUID=58FC18DCFC18B5EA    /media/IMAGES    ntfs-3g    defaults    0    0
UUID=987CEDE67CEDBF5E    /media/FRONTIER    ntfs-3g    defaults    0    0
UUID=5A6096006095E355    /media/ANIME+    ntfs-3g    defaults    0    0
UUID=3E8CA2A58CA256E5    /media/MISC    ntfs-3g    defaults    0    0
UUID=185C4CB05C4C8B08    /media/Data    ntfs-3g    defaults    0    0
UUID=F0E4D73AE4D701B0    /media/Aud-soft-pix    ntfs-3g    defaults    0    0
The partitions that had issues mounting were TEMP1 and TEMP2 - maybe because the volume names were originally "TEMP #1" and "TEMP #2" - I noticed that one of them auto-mounted before, but the other would not.......maybe the special characters in the volume name.

_**GAMING**_
I find almost no gaming on Linux. I can't get STEAM to work on WINE and I am seriously not paying for CEDEGA. If it was a one-time buy then maybe, but that subscription thing is not appealing.

Well that about sums it up. Aside from the issues mentioned I am loving Ubuntu. The Synaptic Package Manager is very nice, and after putting things in place the way I wanted the main things that I keep going back to Windows for is gaming and my password manager. Outside of that - occasionally I get some documents from my office that OpenOffice does open, but the formatting is messed up - so to Windows and MS Office for those.

Any direction or suggestion is most appreciated and I have been going through some material online to kinda familiarize myself with sections of the CLI. Thanks in advance.

---

### Post by waynefoutz on 2010-04-06
try getting Steam with Playonlinux. It's in the Software center application. I had problems myself, but that program set it up for me. Also, just about all of the id software games such as doom 3, the Wolfenstein games, have native executables you can get from id's site. Urban Terror is a great game with a windows and linux executable file in it. This is probably the best FPS for linux, in my opinion. Some of the Wolfenstein mods have look more modern, but Urban Terror is a lot of fun.  [http://www.urbanterror.info/news/home/]("http://www.urbanterror.info/news/home/")
Gaming has come a long way in Ubuntu, but you still have to fiddle around sometimes to get things working.

---

### Post by sdowney717 on 2010-04-06
for windirstat just look at kdirstat
[http://kdirstat.sourceforge.net/](http://kdirstat.sourceforge.net/)

[IMG]http://kdirstat.sourceforge.net/screen-shots/kdirstat-main.png[/IMG]

---

### Post by khat17 on 2010-04-07
Thanks for the responses. 

I have tried PlayOnLinux once before, but then I couldn't uninstall STEAM from it thereafter so I was looking for some alternative. Someone had told me about WINE-X but I can't find that to download. I think I found one link, but I needs to compile it or something before running.....

KDIRSTAT is **EXACTLY** what I was looking for! Many thanks for that! Now if only I could find alternatives for the others.....

As for my USB problems - take this morning for example. I stick in a thumb drive and it doesn't auto-mount. I use MountManager to set the mount point and mount it, then I can't copy anything to it because it says I don't have permissions. Then if I try to unmount it from Nautilus it tells me that I am not root. BUT if I reboot and bring the machine up with the thumb drive plugged in I have full access to it, and I can do all functions with it - the icon will come up as a USB removable storage icon and I can "safely remove" and all that. Weird....

*EDIT*
OK even stranger.........that's not working anymore. In order to get access to my thumb drive I have to mount it with MountManager then run a "sudo nautilus" from the terminal in order to copy files to the thumb drive........

This was an issue with 9.x but right now I'm testing the beta 10.x - I'm not sure why this happens, but I have a strange feeling it has something to do with my volume name for TEMP#1 and TEMP#2 so I may change those and see if it makes a difference after a reinstall.

---

### Post by philinux on 2010-04-07
> **khat17 said:**
> 

Now if only I could find alternatives for the others.....



For Everything.

Places>Search for files, seems to work fine for me.

For exact file checkout the man pages for the command md5sum.

---

### Post by khat17 on 2010-04-07
> **philinux said:**
> For Everything.

Places>Search for files, seems to work fine for me.

I tried that, but I don't see any option to search all mounted systems. If you check as well, EVERYTHING searches all NTFS partitions and gives you real-time results once you start typing. Test it in a VirtualBox or something and see what I'm talking about.

---

### Post by philinux on 2010-04-07
> **khat17 said:**
> I tried that, but I don't see any option to search all mounted systems. .

Click the pull down link on File system. It shows my other hard drive partitions. If you mean all at once I can see that option is not there.

---

### Post by khat17 on 2010-04-07
Ya - all at once is what I had in mind. If you use an NTFS based OS then try using EVERYTHING from the link above to get an idea of what I'm looking for. That program was just genius!

---

### Post by Gunman1982 on 2010-04-07
Just for info: wine-x is the old name of cedega. And as far as I know the subscription thing with cedega is for the updates. So if you buy it once you get the up to date version and if you cancel the subscription you just don't get any more updates. If I'm wrong correct me please.

appdb.winehq.org is a good place to check compability and/or solutions for problems with windows games/apps you want to run with wine.

---

### Post by Calash on 2010-04-07
Games can be difficult, especially if there is no native version for Ubuntu.  Wine does a good job but can take some work to make your games run.

Cedega does somewhat of a better job if you are willing to pay for it.


I ended up dual booting so I could keep my Windows based games.  Not the perfect solution but it works for my situation.

---

### Post by khat17 on 2010-04-11
Well I reinstalled 10.04 and checked to see if the problem came back.

After the install I noticed that two of my partitions did not come up.

Installed MountManager and MM didn't see any of the partitions mounted - even though they were sans 2.

Installed NTFS-CONFIG and had it auto-load all volumes - then use MM to check and found that all volumes were now mounted.

Use MM to save the current configuration and export it to a file, then reboot and check.

Since then all external devices auto-load properly.

No idea what the issue was - here is the current config which you can compare with the one above....

> 
/dev/fd0    /media/floppy0    vfat    noauto    0    0
UUID=A834055834052AC0    /media/PRIMARY    ntfs-3g    defaults    0    0
UUID=01C98F0124170F00    /media/DOCUMENTS    ntfs-3g    defaults    0    0
UUID=58FC18DCFC18B5EA    /media/IMAGES    ntfs-3g    defaults    0    0
UUID=F08A8AA68A8A68C4    /media/MUSIC    ntfs-3g    defaults    0    0
UUID=90D4501CD45006BE    /media/STEAM    ntfs-3g    defaults    0    0
UUID=9CB85196B851702E    /media/BACKUP_TEMP    ntfs-3g    defaults    0    0
UUID=987CEDE67CEDBF5E    /media/FRONTIER    ntfs-3g    defaults    0    0
UUID=F0E4D73AE4D701B0    /media/Aud_soft_pix    ntfs-3g    defaults    0    0
UUID=3520CFFC53737FD1    /media/Data    ntfs-3g    defaults    0    0
UUID=94E0D21AE0D20302    /media/TEMP1    ntfs-3g    defaults    0    0
UUID=02C80807C807F825    /media/TEMP2    ntfs-3g    defaults    0    0
UUID=5A6096006095E355    /media/ANIME+    ntfs-3g    defaults    0    0
UUID=3E8CA2A58CA256E5    /media/MISC    ntfs-3g    defaults    0    0
UUID=8b6fe09f-196b-427d-bbbe-e88c4c239e0b    /    ext4    defaults    0    1
UUID=08fa8c3a-d8f2-45fb-ae67-cdcf9e5801e8    swap    swap    sw    0    0
Aside from the ordering, I see no difference between the two config files.....so still no idea why it was behaving the way it did.

Gonna setup some other stuff now, but notice that the x86 and x64 versions have some differences (need x64 apps for the x64 version for some apps) but that's minor.  Continuing the testing.

*EDIT*

So now I'm down to trying to find apps like 

[EVERYTHING]("http://www.voidtools.com/")
[EXACTFILE]("http://www.exactfile.com/")
[Large Software Password Manager]("http://www.largesoftware.com/html/passwordmanager.html")

And then I'd only have my gaming needs on Windows.

---

### Post by khat17 on 2010-04-24
I also notice that some websites don't load properly for some reason - works fine on the M$ platform tho...maybe it's some encoding or something else I need to download?

[SPEEDTEST.NET]("http://speedtest.net/") and [JNBS]("https://www.jnbslive.com/") for example.
[URL="http://speedtest.net/"]
SPEEDTEST.NET[/URL] and other sites will not allow me to press the flash buttons. 

[JNBS]("https://www.jnbslive.com/") and other sites have the login button at the wrong position on the screen. Will post screenies later on.

*EDIT*

Some of the issues I had with the mounting and such have gone since I got the updates. Finally got faster internet - that was hampering me and not allowing me to get the updates.

---

### Post by khat17 on 2010-05-03
Well the FLASH pages like SPEEDTEST were fixed after doing some searching [and following this link]("http://ubuntuforums.org/showthread.php?t=1358591").

Basically....

> 
1. Open Terminal
sudo -i apt-get purge flashplugin-installer nspluginwrapper

2. Download File
wget [http://dl.dropbox.com/u/1207653/wordpress/Get64bitFlash-0.2.3.tar.gz](http://dl.dropbox.com/u/1207653/wordpress/Get64bitFlash-0.2.3.tar.gz)

3. Extract File
tar -xzf Get64bitFlash-0.2.3.tar.gz

4. Install
./Get64bitFlash
That sorted out the problem. I'm running 64bit and the Flash Player installed was 32. Interesting.

Still nothing on the encoding for the page. Pics in a few after I reboot into Windoze.

[SIZE=5]Windows[/SIZE]
[IMG]http://i162.photobucket.com/albums/t263/khat17/JNL-Windows.png[/IMG]

[SIZE=5]Ubuntu[/SIZE]
[IMG]http://i162.photobucket.com/albums/t263/khat17/JNL-Linux.png[/IMG]

As you can see there seems to be an issue in the page encoding or something. If I disable images it loads the positions fine tho....

---

