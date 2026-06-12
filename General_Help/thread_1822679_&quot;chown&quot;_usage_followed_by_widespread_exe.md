---
title: "&quot;chown&quot; usage followed by widespread execution problems"
date: 2011-08-10
forum: General Help
---

### Post by champost on 2011-08-10
Hi all/anyone,

I've recently tried to install Matlab for Linux on my laptop (running Ubuntu 11.04). I anticipated write privileges for */usr/local/* which is the default install location for Matlab. After taking a quick look at *man chown* in order to enable a smooth install from my non root account *aham*, I fiddled with the following commands:

[I]aham@mycomp:~$ sudo chown -R aham /usr/
aham@mycomp:~$ sudo chown -R root /usr/
aham@mycomp:~$ sudo chown -R aham /usr/local
aham@mycomp:~$ sudo chown -R root /usr/local[/I]

While doing the above, *sudo* broke down by saying "*sudo: must be setuid root*" which I bypassed using *su* to change over to *root*. A little later, to my amazement, plenty of installed programs stopped executing altogether (synaptics, chromium browser, virtualbox, ...) and Ubuntu would refuse to restart the machine correctly from "*aham*". 
The group/account settings were also inaccessible and a split second appearance of a window warned, "*You need to authenticate to modify the system configuration*...". Since, I tried to fix *sudo* from *root* by following [this remedy]("http://www.review-ninja.com/2009/03/sudo-error-sudo-must-be-setuid-root.html") and it worked fine but the rest of programs still don't execute...

Any help would be greatly appreciated!
champost

---

### Post by champost on 2011-08-10
Here is yet another update for my problem, I tried running a program which doesn't work currently (e.g. chromium) from *root* and this is what I get:

[I]root@mycomp:/usr/bin# ls chr*
chromium-browser  chrt
root@mycomp:/usr/bin# ./chromium-browser 
[5347:5347:8762184641:FATAL:zygote_host_linux.cc(128 )] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /usr/lib/chromium-browser/chromium-browser-sandbox is mode 4755 and owned by root.
Aborted
root@mycomp:/usr/bin#[/I]

Thanks
champost

---

### Post by sisco311 on 2011-08-10
Backup your data and reinstall Ubuntu (30-40 minutes).

Your other option is to manually fix the ownership and permissions of all files in /usr (a few days).

---

### Post by champost on 2011-08-11
Hi

Thanx for the quick reply. I was keeping the reinstall option as a last resort as it requires some (a lot of ?) backup beforehand. 
Would you be having any suggestions on what to back up other than the *home* folder, the synaptics list of installed applications and the sources.list file? Many other topics on the forum propose the following...

[I]/var/cache/apt/archives
/opt/
/etc/[/I]

Thanks again
champost

---

### Post by jwbrase on 2011-08-11
> **champost said:**
> 
Would you be having any suggestions on what to back up other than the *home* folder, the synaptics list of installed applications and the sources.list file? Many other topics on the forum propose the following...

*/var/cache/apt/archives*

Backing this up will help Synaptic restore the installed applications faster, as it won't have to redownload as much stuff, but it's not essential. (Though it may be *very* helpful depending on the speed of your internet connection).

> 
*/opt/*


Anything in this directory that doesn't have a corresponding package in Synaptic should be backed up. It may well be empty, and even if it isn't, everything in it may have been installed through Synaptic. (I only have two directories under /opt, and both correspond to packages installed through Synaptic).

> 
*/etc/*

This stores a fair number of system settings. Backing it up is, again, not entirely essential, but might prove quite helpful in restoring your original configuration.

---

### Post by champost on 2011-08-12
How do I get all (or most of) my old system settings (*/media/backup/etc*) back into the current settings (*/etc*) given that 
1° I now have a fresh install of Ubuntu 11.04 and 
2° my username (*aham*) doesn't have the necessary sudo privileges for copying the files into */etc* ? Also, do I have to copy all the files ?

Is it simpler doing the file transfer by using *su* or will I once again end up messing my settings ?

---

### Post by The Cog on 2011-08-12
My first reaction would be to suggest
```
sudo cp -a /media/backup/etc /etc
```
but if you don't have the rights to sudo then you can't do that. If the root account has been given a password (the default Ubuntu install doesn't give a password to root) then you could do:
```
su -l
cp -a /media/backup/etc /etc
exit
```

In either case, it might be a good idea to make a backup of /etc before restoring the backup:
```
cp -a /etc /etc-backup
```

---

### Post by jwbrase on 2011-08-12
> **champost said:**
> How do I get all (or most of) my old system settings (*/media/backup/etc*) back into the current settings (*/etc*) given that 
1° I now have a fresh install of Ubuntu 11.04 and 
2° my username (*aham*) doesn't have the necessary sudo privileges for copying the files into */etc* ? Also, do I have to copy all the files ?

Did you create an account with administrator privileges during the installation?

> 
Is it simpler doing the file transfer by using *su* or will I once again end up messing my settings ?

You won't be able to use su unless you have a root password or are su-ing from an account that can use sudo.

Anyhow, if all else fails, you should be able to boot into recovery mode (hold down shift during boot to get a grub menu, then select a boot entry with "(recovery mode)" after it. Eventually you'll get a text-mode menu: select "root", and you should get a root console.

---

### Post by champost on 2011-08-12
I don't remember Ubuntu asking me during install if I wanted admin status for my user account. But it does ask me in a dialog box for a username, a password for the username, a hostname and if I would like to encrypt my home folder...(unless I'm missing out stuff)

As for using *su*, I ran it (for the first time) just to set a root password.

By the way, I followed The Cog's suggestion for *cp - a* from *root* for the */media/backup/etc* to */etc* file transfer but then I fail to see any difference in system settings (i.e. getting back old settings). What should I expect under "ideal conditions" ?

---

### Post by dino99 on 2011-08-12
I suppose you have learn that tweaking too deeply the default installation settings breaks the whole system. Your data & settings are secure insde your /home partition, if you dont have one then you need to backup your own work and format the partition system installation ( "/")

the installation might be:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by champost on 2011-08-12
Yes Sir! I am atoning for my "sins" now!

Initially I had a 2 partitions (a general + a swap one). I did a fresh install of Ubuntu (choosing no disk partition) before which  I backed up all the data within /home, so I don't understand the > **dino99 said:**
> ... settings are secure inside your /home partition part of your statement.

Do you mean some settings are still accessible ? somewhere in */media/backup/home* or the freshly installed */home* ?

---

### Post by The Cog on 2011-08-12
> **champost said:**
> By the way, I followed The Cog's suggestion for *cp - a* from *root* for the */media/backup/etc* to */etc* file transfer but then I fail to see any difference in system settings (i.e. getting back old settings). What should I expect under "ideal conditions" ?
Well, that should have restored a lot of your old system settings. I would be inclined to reboot immediately after restoring /etc. Any system settings that didn't get restored that way, well I guess you'll just have to set them again. I hope that's not too many. 

Actually, it occurs to me that if the package manager database is stored under /etc (not sure on that), you might be restoring a package database that doesn't actually reflect what is now installed, which might cause problems. I wonder if restoring /etc is worth it at all. Others might have a better feel for this than I do

---

### Post by jwbrase on 2011-08-12
> **champost said:**
> I don't remember Ubuntu asking me during install if I wanted admin status for my user account. But it does ask me in a dialog box for a username, a password for the username, a hostname and if I would like to encrypt my home folder...(unless I'm missing out stuff)

As for using *su*, I ran it (for the first time) just to set a root password.

By the way, I followed The Cog's suggestion for *cp - a* from *root* for the */media/backup/etc* to */etc* file transfer but then I fail to see any difference in system settings (i.e. getting back old settings). What should I expect under "ideal conditions" ?

/etc holds lots of system-wide settings. User specific settings (desktop appearance, etc.) will generally be in hidden files and folders in your home directory.

---

### Post by champost on 2011-08-12
Hi
Actually I wasn't very far from an almost complete recovery of my settings.

1) I had missed out on the hidden files (.*) in the */media/backup/home* folder which I eventually copied using a doubly cautious visual approach (*cp -prfv /source /destination*)
2) I also hadn't rebooted immediately as The Cog suggested
3) Finally the */media/backup/etc* only created more problems as The Cog correctly guessed in his post and I excluded it completely. I also didn't bother about */var/cache/apt/archives* as I have a good internet connection and as I had saved a comprehensive synaptics marker file.

I also followed dino99's suggestion by creating a 3 way partition (*/root*, *swap* & */home*) of my hard disk for the fresh install of Ubuntu (for future recoveries...).

And thanks to you guys I now have a system up and working with my previous settings (with a few permissions to be reset for some executables).

cheers
P.S. I shall be marking this thread as solved soon unless you have some comments to make...

---

### Post by The Cog on 2011-08-13
Good news. And thanks for the feedback.

---

