---
title: "Package/program backup/restore question"
date: 2010-04-28
forum: General Help
---

### Post by holadebob on 2010-04-28
I am noob, have been studying this system in spurts, but really busy on other projects, so maybe someone out there can enlighten me on a basic process with Ubuntu. 

I want to backup all my downloaded programs including their config files in case of disaster like what I just went through. Backup methods for Ubuntu are a little confusing to me I think because I don't understand the process. Simple backup is not simple nor did it restore my files (said files didn't exist at the location they were in), even though Nautilus showed them to be intact in the dir I sent them to. I couldn't find out how to restore the programs (selectively if possible)

So, anyway, I don't need data backup for my personal files, fotos, etc., they are all in one directory on desktop and I back them up every day or so. I don't need to back up Ubuntu 9.10, cause I have the installation disk. But, I do need to back up my programs somehow.

Sorry for the long background, but here's the question - Can I copy my installed programs and then paste them back on a new installation?

I guess what I really want to know is how are programs installed - is the entire installation for each program contained in one directory? If I copy the lib files and find and copy the program file directory, can I just write them back after new install?

Thanks for reading my woes

---

### Post by dv3500ea on 2010-04-28
Run this command to get a backup file of your packages
```

perl -e '
open (my $in, "-|", "dpkg --get-selections") || die $!;
while (<$in>) {
    s/\t/\n/;
    s/\t//g;
    my @arr = split(/\n/);
    if ($arr[1] eq "install") {
         print "$arr[0] ";
    }
}' > packages.backup

```
and this command to restore it
```
sudo apt-get install `cat packages.backup`
```

Generally, to save your settings you will need to back up the '/etc' folder and all the hidden files and folders (names begin with '.') in your home directory.

To do this you could run
```

sudo tar cvf system-settings.tar /etc
tar cvf user-settings.tar ~/.*

```
and to restore run
```

sudo tar xvf system-settings.tar
tar xvf user-settings.tar

```

---

### Post by holadebob on 2010-04-28
I ran the backup script for the package.backup, but no results, no indication it ran, just went back to the prompt. Where would the file go, I don't see a destination in the script, but then I don't know much about C.

---

### Post by dv3500ea on 2010-04-28
The file is called packages.backup and will be created in the current working directory.
To successfully restore the files you need to have them in your working directory.
If you have a specific backup folder run
```
cd path-to-backup-folder
```
before running the backup or restore commands.

---

### Post by holadebob on 2010-04-28
This is where my noobie status really shows - which is the working directory? Home?
I ran a search files for packages.backup and came up zilch.

---

### Post by dv3500ea on 2010-04-28
It is generally the first place where files are created or read from.
In a terminal you can find the working directory by entering ```
pwd
```
by default this is your home folder but the command 'cd' changes this.
Enter ```
ls
``` to view the contents of the working directory.

---

### Post by holadebob on 2010-04-28
Ok, that makes sense, thanks. Also the packages.backup is in there :), but it contains only a list of the programs that I have installed, not the actual programs. There's something missing in my understanding here, I think. If I have a list of the programs, I can go to Synaptic and line by line install them again, but what I would really like is to be able to reinstall them automatically from a backup file. Sure hope I'm making sense here - thanks for your patience...

---

### Post by dv3500ea on 2010-04-29
```
sudo apt-get install `cat packages.backup`
```
is the command to restore installed programs by reinstalling them from the internet
It does basically the same thing as installing them one by one in synaptic, but it is automated.

---

### Post by SteveWh on 2010-05-01
**holadebob**, not sure if you have the same concern I do, but this info might help. For me, the problem is re-downloading installed packages because I'm on dialup internet. It takes days.

In Synaptic Package Manager, somewhere in Preferences is the option to save all downloaded packages (i.e. not delete them after installation). I made sure that option is selected.

After download, the .deb files are saved in this directory: 

/var/cache/apt/archives/

Incomplete downloads are in /var/cache/apt/archives/partial/ until they complete.

What I've done is copy the .deb's to a DVD. Then, if I need to reinstall Ubuntu, I should be able to copy the .debs back to their cache folder. I'll still have to reinstall them, but at least it avoids the downloading.

In Synaptic Package Manager, there is a way to generate a list of all your installed packages. The same thing can be done using apt-get. apt-get also allows using the saved list to reinstall the named packages. 

Sorry to be vague about that. I haven't got to that point yet. But I do think it's going to be possible to automate package reinstallation after a crash. 

The settings and preferences for each individual program (the config files you mentioned) are stored in each user's home directory. My /home is a separate HD partition, so the config files weren't affected by the crash I'm cleaning up from, and the applications are able to use them again after reinstallation. 

Some other config files (some application ones, and very important system ones) are stored in /etc/, so I've also made a DVD of that entire directory. Example of the importance of that: After Ubuntu reinstall, I was able to copy these files from DVD: group, group-, gshadow, gshadow-, passwd, passwd-, shadow, shadow-, and instantly (after setting the permissions properly) all my users and groups were back, same as they were before the crash!

I suspect this method is probably safer and less hassle than the method you're considering, trying to make copies of the .libs and binary executables, to put them back. Partly because if you only restore the executables, the package manager might end up with no record of them being installed (?).

---

### Post by holadebob on 2010-05-01
Steve, your insight really helps a lot. I found in synaptic under Settings,Preferences,Files an option to leave all downloaded packages in cache, but I don't know if the package is installed at the time with a copy in cache, or does it just leave it in cache for me to install later. Is that what you are talking about?

How to initiate the installation of the packages from the saved location sounds like a challenge. 

It would be really really nice to be able to download all my packages, and then copy them for future installation.
 
I live in the boonies and service here is not too stable, and I like to play with this system as I'm learning it, which means I will probably lose my system again. The last time I reinstalled 9.10, I mixed up the /root/ and /home/ partitions, which are about the same size, and installed without formatting. Which meant some duplicate file work, but I lost all the programs, and it took a while to download them to get back in smooth op again.

There has been so much discussion on backup systems for Linux on this board and other places, and I've tried lots, but have never got that confidence level where I can relax with the restore process. I know a lot of it is ignorance, but I do know that I personally don't need a sophisticated compression type of backup with jillions of options. I just need a disk of my programs for reinstall and a copy of my personal folder(which I always keep copied on dvd), and the livecd. I should probably make a copy of /home/, but haven't done that yet, will do it today.

Thanks for the ideas..

---

### Post by SteveWh on 2010-05-01
> **holadebob said:**
> I found in synaptic under Settings,Preferences,Files an option to leave all downloaded packages in cache, but I don't know if the package is installed at the time with a copy in cache, or does it just leave it in cache for me to install later. Is that what you are talking about?
Yes, as you download the packages, they're downloaded to the /partial directory. When the download completes, they're moved to the /archives dir (full paths given in previous post). When you install them, they're unpacked and installed from /archives, but the original .deb files remain there permanently. Even if you uninstall the applications, the .debs are still left in /archives. 

So /archives contains anything you've downloaded. If you reinstall a package, it's installed from /archives again. So if a crash and Ubuntu reinstall causes you to lose what was in /archives, you can just copy the .deb files back to that folder from DVD. Then mark and install them in Synaptic as usual, which will use the copies in /archives again. 

> How to initiate the installation of the packages from the saved location sounds like a challenge. 

It would be really really nice to be able to download all my packages, and then copy them for future installation.
 Right, that's what the above will do. Copy all the .deb files from /archives to a DVD for backup.

I think I was wrong about apt-get saving/reading the list of packages to install. Synaptic certainly can do it, using File > Save Markings and Read Markings. (In the Save dialog box, the Full State (?) option saves not just your current new markings, but the state of every package). The resulting text file contains the list of packages and their state (installed or not, etc.) A command line program can do it, too; ran across the instructions the other day, but it doesn't seem to be apt-get. Maybe it was dpkg. After you have that list saved somewhere, dpkg (or whatever the proper application is) can, I think, read the list and automatically restore all the packages to their previous state, installing whatever is necessary.

The application config files in /home have dots in front of their name; they're hidden files and folders. In Nautilus Preferences, select Show Hidden Files.

---

### Post by fyo on 2010-05-01
Creating a backup of an INSTALLED program is a b*tch.

Unless we're talking very, very simple programs, it's simply not worth the trouble. (The issues are similar in Windows and Mac OSX).

You have basically two options: 

1) Save the package files (typically .deb) and make a backup of them.

2) Make a backup of your entire system.

The former doesn't get you the settings and configurations (typically located in /etc or various . files/folders (.vimrc, .bashrc etc) in your home directory. Backup up /etc and your home folder (possibly leaving out a few things, e.g. /Desktop, if you have a lot of stuff there and are backing it up separately).

NOTE: To use only the already downloaded package files, add "--no-download" to the apt-get command suggested by dv3500ea. Or you can just use Nautilus (file manager/browser) and double-click on the .deb files).

The latter takes up quite a bit more space, but you can do a lot to optimize the process. I've used Clonezilla to great effect in the past.

---

### Post by holadebob on 2010-05-01
Wow, everything is now clear. Steve and fyo, thank you so much. I think I have learned enough to get my system ready for the next crash. :) 

I'll solve this page if you no more to add.

buen dia
Bob

---

### Post by dv3500ea on 2010-05-01
Just a note: to make your life easier you can [install]("apt://aptoncd") [APTonCD]("http://aptoncd.sourceforge.net/") (from synaptic)

---

### Post by holadebob on 2010-05-01
dv3500, APTonCD is nice, I just saved all my packages, dependencies, etc. on a CD.
To restore, apparently I need to install each of the programs individually through Synaptic.
 
Do you know if there is a way to install all of the programs that I would have put back into /var/cache/apt/archives/? with one operation/command?

Thanks for the headsup on APTonCD - it makes things a little smoother.
Bob

---

### Post by dv3500ea on 2010-05-02
Insert the cd/dvd.
Open it up in the file manager to find out what path it is on (eg /media/cdrom)
and run
```

cd /media/cdrom
sudo dpkg -i *.deb

```
replacing '/media/cdrom' with the path you found

---

### Post by grnorris on 2010-10-20
Glad I found this.  I don't have the dial-up issue so I'll just use the script presented by [dv3500ea]("http://ubuntuforums.org/member.php?u=906606")

I'm currently importing programs and settings from a real Ubuntu 10.04 [64-bit] installation to a Virtual Ubuntu 10.10 [32-bit] installation (Virtual Ubuntu is running with Newest non-OSE VirtualBox on Win7 host).  If you could please verify the scripts

```
perl -e '
open (my $in, "-|", "dpkg --get-selections") || die $!;
while (<$in>) {
s/\t/\n/;
s/\t//g;
my @arr = split(/\n/);
if ($arr[1] eq "install") {
print "$arr[0] ";
}
}' > packages.backup
```and 

```
sudo apt-get install `cat packages.backup`
```will work for importing programs from Ubuntu 10.04 [64-bit] to Ubuntu 10.10 [32-bit]

Also could you please give me a script that similar to your backup of /ect script makes a backup of /ect but, also makes a backup of the home folder (I'm assuming that so long as I'm signed in the built in encryption won't make a difference).  It's a single user machine so the only folder under home is my user home folder.

I will manually go through and pull out the files I need when importing as I'm going for a slightly different setup with the VM (I'm considering trying fxce or KDE as they apparently work better with seamless mode).  I'd code these myself but, I've not the time right now to learn that kind of coding (I'm pretty fluent in Java and know some MS Batch but, only know a few basic commands in linux).

Also, you'll notice I'm going from 64 to 32 bit, this is because the 64-bit Ubuntu has compatibility issues with most current software and I can't won't be utilizing my full 4GB of RAM in the VM.  Also, in case you're wondering the virtual Ubuntu seems to be running at good speeds and I didn't notice any issues with 3D (as some people warned about in another thread).

---

### Post by grnorris on 2010-10-21
> **grnorris said:**
> Glad I found this.  I don't have the dial-up issue so I'll just use the script presented by [dv3500ea]("http://ubuntuforums.org/member.php?u=906606")

I'm currently importing programs and settings from a real Ubuntu 10.04 [64-bit] installation to a Virtual Ubuntu 10.10 [32-bit] installation (Virtual Ubuntu is running with Newest non-OSE VirtualBox on Win7 host).  If you could please verify the scripts

```
perl -e '
open (my $in, "-|", "dpkg --get-selections") || die $!;
while (<$in>) {
s/\t/\n/;
s/\t//g;
my @arr = split(/\n/);
if ($arr[1] eq "install") {
print "$arr[0] ";
}
}' > packages.backup
```and 

```
sudo apt-get install `cat packages.backup`
```will work for importing programs from Ubuntu 10.04 [64-bit] to Ubuntu 10.10 [32-bit]

Also could you please give me a script that similar to your backup of /ect script makes a backup of /ect but, also makes a backup of the home folder (I'm assuming that so long as I'm signed in the built in encryption won't make a difference).  It's a single user machine so the only folder under home is my user home folder.

I will manually go through and pull out the files I need when importing as I'm going for a slightly different setup with the VM (I'm considering trying fxce or KDE as they apparently work better with seamless mode).  I'd code these myself but, I've not the time right now to learn that kind of coding (I'm pretty fluent in Java and know some MS Batch but, only know a few basic commands in linux).

Also, you'll notice I'm going from 64 to 32 bit, this is because the 64-bit Ubuntu has compatibility issues with most current software and I can't won't be utilizing my full 4GB of RAM in the VM.  Also, in case you're wondering the virtual Ubuntu seems to be running at good speeds and I didn't notice any issues with 3D (as some people warned about in another thread).

Never mind the backup of settings.  I failed to realize that you were adding the home directory with the second command (I forgot about the generic representation using ~./)

As far as the download script goes I must made a download script using Synaptic and will try to install via synaptic individual packages.

---

### Post by dv3500ea on 2010-10-21
> **grnorris said:**
>  If you could please verify the scripts

...

will work for importing programs from Ubuntu 10.04 [64-bit] to Ubuntu 10.10 [32-bit]



Yes, they should work fine because the packages are redownloaded from the internet and so will be for the correct version and architecture.

---

