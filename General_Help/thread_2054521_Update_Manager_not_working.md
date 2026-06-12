---
title: "Update Manager not working"
date: 2012-09-07
forum: General Help
---

### Post by Olthar on 2012-09-07
So, I tried downloading some updates, but it just didn't work. When it tried to install them, it crashed and gave a message:

**Not all changes and updates succeeded.**

In the details, I got:

```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
files list file for package 'liblash2' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying recover:
```

Any help would be much appreciated.

---

### Post by Epodx64 on 2012-09-07
strange try this from a console

sudo apt-get update 
sudo apt-get -f upgrade

---

### Post by Olthar on 2012-09-07
Okay. How do I open the console?

...Yes, I don't really know much about how this all works. :P

---

### Post by jockyburns on 2012-09-07
Ctrl + Alt + t  should open a terminal, when you type in the sudo commands you'll be asked to enter your password. When you type your password in, it will look like nothings being typed. Don't panic, it just doesn't show your password (not even as a row of asterisks)

---

### Post by Olthar on 2012-09-07
"apt-get update" got a big list of stuff to pop up, but when I tried "apt-get -f upgrade," I just got the same error message as when using the Update Manager.

---

### Post by Olthar on 2012-09-07
Anyone? Help?

---

### Post by plucky on 2012-09-07
Try ```
sudo apt-get clean
sudo apt-get install -f
```

and post the output from the second command.

Good Luck

---

### Post by Olthar on 2012-09-07
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
ggz-gnome-client python-smartpm
Use 'apt-get autoremove' to remove them
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
```

---

### Post by plucky on 2012-09-07
Now try ```
sudo apt-get upgrade
``` and again post output in [noparse]```

```[/noparse] brackets.

Good Luck

---

### Post by Olthar on 2012-09-07
I got a long list of what appeared to be installation of the upgrades, but right as it hit 99%, it crashed and gave the original error message.

---

### Post by plucky on 2012-09-07
Try opening Synaptic Package Manager and select **Edit > Fix Broken Packages** and see if that corrects the problem.

Although on my 12.04 system, there is no liblash2 package.

Good Luck

---

### Post by Olthar on 2012-09-07
That did absolutely nothing. :(

---

### Post by Olthar on 2012-09-07
Should I try to remove the package and see if that works?

---

### Post by plucky on 2012-09-07
> **Olthar said:**
> Should I try to remove the package and see if that works?

No harm in trying.

---

### Post by Olthar on 2012-09-07
Nope. That didn't work. I got the same error message, and nothing happened.

---

### Post by Olthar on 2012-09-07
Is there some way to try deleting it without the Synaptic Package Manager?

---

### Post by Olthar on 2012-09-07
Is anyone going to help me? :(

---

### Post by Bashing-om on 2012-09-07
yeah, after a lot of time and effort I am beginning to get a handle on this.

Firstly I find that the liblash package is no longer available within ubuntu.
last I found of it was in version 10.10...
any specific details in relation to installing this package ?

What version of ubuntu are you using  and what system...,,and I should have a fix for you.


[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-07
I'm using 10.04. I would have upgraded to 12.04, but, well, my Update Manager isn't working. :(

---

### Post by Bashing-om on 2012-09-07
Firstly, lets get your system stable.
Secondly, The commonly advocated process to go from 10.04 to 12.04 is to do a clean install (the differences between kernels and support packages is huge=>a lot can go wrong)//
-----------------
lets do this:
#get rid of the error
```
sudo apt-get remove liblash2 
```
then this:
oldfred's methology for restoring:
Then try ( all the # are comments do not type anything after a #)
#if not chroot use: /chroot not to be used by new users/
sudo -i
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
All that does is update it again.
#log-out from super user
exit 
.......
run these and advise status.
hopefully 12.04 (attempted upgrade) has not made an impression on your present system.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-07
It said liblash2 is not installed so it can't be removed. :/

Should I still do that second part then?

---

### Post by Bashing-om on 2012-09-07
no on the other part. lets take care of the error first.... hang on a bit more ..I will boot up 10.04 see what I can find be back soonest................

off topic: thunder storms in my area ... may have to cease and desist for the eve.


BDQ

---

### Post by Olthar on 2012-09-07
Alright.

And thanks for the help. :)

---

### Post by Bashing-om on 2012-09-07
I booted up 10.04 //found no trace on liblash2 .....huuummmmm

I got something else in mind to do to try and fix this, but, first let's look and see what kernel version you have. Post the output of:
```
uname -a
```

[INDENT]hangin' in there <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-07
```
Linux ninjalord-desktop 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i 686 GNU/Linux
```

---

### Post by Bashing-om on 2012-09-07
Good .. the kernel remains as 10.04...
as we can not seem to delete the offending liblash2 dependency ...let's give it something to work with...install that sucker and see if the error goes away!
```
sudo dpkg -i liblash2
```

If it installs with no error in relation to liblash2 ..then we can proceed to clean up the update mess.

                                     BDQ

---

### Post by Olthar on 2012-09-07
```
dpkg: error processing liblash2 (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
liblash2
```

---

### Post by Bashing-om on 2012-09-08
I have thought about it ...IF you were to do in terminal:
```
apt-cache search liblash2
```you would see that the package is available...
soooo..that tels me that your sources.list file is corrupt.
to fix your sources.list file do this:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
sudo apt-get clean
sudo apt-get update

```that purges the related files and "apt-get update" regenerates the ones required.

Now is your system stable ?

                                                      regards <==BDQ

---

### Post by Olthar on 2012-09-08
Nope. :(

---

### Post by Bashing-om on 2012-09-08
Olthar;

  shheeesh//
It is late here and I am going to put-it-between-the-sheets..will think on this a bit ...
after my morning chores I will check back in; See what the haps are at that time...



                                   CUL

---

### Post by Olthar on 2012-09-08
Goodnight. :)

I was actually about to head off to bed, anyways.

---

### Post by raja.genupula on 2012-09-08
> **Bashing-om said:**
> Good .. the kernel remains as 10.04...
as we can not seem to delete the offending liblash2 dependency ...let's give it something to work with...install that sucker and see if the error goes away!
```
sudo dpkg -i liblash2
```

If it installs with no error in relation to liblash2 ..then we can proceed to clean up the update mess.

                                     BDQ

Well actually if you'd like to install a .deb file then you have to run 

```
sudo dpkg -i filename.deb 

```

For this case ```
sudo dpkg -i liblash2.deb
```

@OP have look in Synaptic for this package ?

---

### Post by raja.genupula on 2012-09-08
> **Olthar said:**
> So, I tried downloading some updates, but it just didn't work. When it tried to install them, it crashed and gave a message:

**Not all changes and updates succeeded.**

In the details, I got:

[B]Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
files list file for package 'liblash2' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying recover:[/B]

Any help would be much appreciated.

try this 

```
sudo dpkg -r liblash2
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Olthar on 2012-09-08
> **raja.genupula said:**
> @OP have look in Synaptic for this package ?
There is a liblash2, but I don't know if it's a .deb file.

> **raja.genupula said:**
> try this 

```
sudo dpkg -r liblash2
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```
After the first command:
```
dpkg: warning: ignoring request to remove liblash2, only the config
files of which are on the system Use --purge to remove them too.
```

---

### Post by raja.genupula on 2012-09-08
look in your synaptic for that pkg ?

---

### Post by Olthar on 2012-09-08
Yeah.

> **Olthar said:**
> There is a liblash2, but I don't know if it's a .deb file.

---

### Post by Olthar on 2012-09-08
Help please. :(

---

### Post by Bashing-om on 2012-09-08
Olthar;

 I am back for a few ... been looking for a way to isolate the error of that liblash2 package. See what results these commands return.
```

dpkg -l |grep liblash2
ps ax | liblash2

```

By the way, I realize how time consuming, frustrating and troublesome this trouble shooting is// Bear in mind we are seeking a solution to a problem.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-08
First command:
```
pc  liblash2                                   0.5.4-0ubuntu5
                    Linux Audio Session Handler (LASH) shared library f
```

Second command:
```
liblash2: command not found
```

I know. Thanks for your help. :)

---

### Post by AleBuenosAires on 2012-09-08
I have a similar problem.

No se ha podido inicializar la información de los paquetes
 
 Ha ocurrido un problema imposible de corregir cuando se inicializaba la información de los paquetes.
 
 Por favor, informe de esto como un fallo en el paquete «update-manager» e incluya el siguiente mensaje de error:
 
 'E:Tipo «b-src» desconocido en la línea 1 de lista de fuentes /etc/apt/sources.list.d/libreoffice-libreoffice-prereleases-precise.list'

En inglés,

Failed to initialize the package information

 Had a problem impossible to correct when initializing the package information.

 Please report this as a bug in the package 'update-manager' and include the following error message:

 'E: Type' b-src "known on line 1 in source list / etc / apt / sources.list.d / libreoffice-libreoffice-prereleases-precise.list '

I don't know what to do.

Need help please!

---

### Post by Bashing-om on 2012-09-08
@AleBuenosAires; Hi!

  The instruction in #28 of this thread should resolve your situation starting at apt-get clean. 


@Olthar ....We know the liblash2 package is installed for sure now ,,, ok, another command to try and remove it:
```

sudo dpkg --remove --force-remove-reinstreq liblash2

```as it is not running (no surprise) will take some more digging to isolate it in the event the above proves unproductive.

Depending on the results from the above command ,,, we may run:
```

sudo apt-get --fix-missing install

```and then I want to see the results from:
```

sudo apt-get check

```[INDENT]still trying <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-08
<ignore>

---

### Post by Olthar on 2012-09-08
First command:
```
dpkg: warning: ignoring request to remove liblash2, only the config files of which are on the system Use --purge to remove them too.
```

Second command:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
ggz-gnome-client python-smartpm
Use 'apt-get autoremove' to remove them
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
```

Third command:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
```

---

### Post by Bashing-om on 2012-09-08
Olthar;

  Wow, this is getting stranger alla-the-time !

  Let's take dpkg's advise and try (again!) :
```
sudo apt-get --purge remove liblash2
```


BDQ

---

### Post by Olthar on 2012-09-08
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package liblash2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
ggz-gnome-client python-smartpm
Use 'apt-get autoremove' to remove them
0 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
```

---

### Post by Bashing-om on 2012-09-08
Sheeesssh ... but we know that the package is installed.// Lemme do some more looking and see what I find about apt-get not finding this package! Let me consider the update cache and what to do >>>

[INDENT]BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-08
Okay. I'm sorry I'm being such trouble. I don't even know what happened. :(

---

### Post by Bashing-om on 2012-09-08
It is not a trouble, It is a legitimate problem; albeit a very vexing one!

I ran across a new one to me that I suggest we try:
```

sudo dpkg --force-all -P liblash2
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a

```if the dpkg -- force command returns errors, there is no point in running the remaining commands. 
[INDENT]man I hth <==BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-08
```
(Reading database ... 90%dpkg: unrecoverable fatal error, aborting:
files list file for package 'liblash2' is missing final newline
```

---

### Post by Bashing-om on 2012-09-08
Yikes!

  This is certainly a learning experience.
I dislike using a sledge hammer to drive a nail ,,,,but I have a BFH in my tool box that I could resort to. But prefer to find a solution; That hammer to be applied before I give up and you do a 
a. re-install 10.01
b. clean install of 12.04 (from cd/usb).

Back to the drawing board, see what else I can come up with.

[INDENT]later <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-08
I don't think I'd be able to do that. I don't actually have any install disks of Ubuntu. I borrowed a disk of 8.04 from a friend several years ago. :/

---

### Post by Bashing-om on 2012-09-09
To get you a disk should not be a big deal (just download the .iso and burn the .iso as image to a cd).

To problem at hand, Run this command / might work,,, 
```

sudo dpkg --clear-avail && sudo apt-get update

```I found a lead on what I was looking for ... I am putting it together  (Edit the file /var/lib/dpkg/status) looking promising; But, it will be tomorrow before I can get back to you with the result.

---

### Post by Olthar on 2012-09-09
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```

---

### Post by Bashing-om on 2012-09-09
I am back and working on the solution.
            Basic trouble shooting
1. We have determined that liblash2 is installed.
2. dpkg is unable to relate to it.
4. dpkg is telling us why (note to self: pay more attention to generated errors)
5. dpkg is telling us why and needs help.
6. dpkg tells us a file is corrupted (but not which one)


so, got to isolate the required file and fix OR replace it.

presently looking at  /var/lib/dpkg/info and comprehending how it does relate as well as other control files related to dpkg.

While I am looking, Take a look yourself at the file "status" located at /var/lib/dpkg/status ;The stanza for liblash2 / what is the difference in this entry as opposed to other stanzas ?
[INDENT]BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-09
```
Package: liblash2
Status: purge ok config-files
Priority: optional
Section: libs
Installed-Size: 104
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: lash
Version: 0.5.4-0ubuntu5
Config-Version: 0.5.4-0ubuntu5
Replaces: liblash
Depends: libc6 (>= 2.4), libreadline5 (>= 5.2), libuuid1 (>= 2.16)
Conflicts: liblash
Description: Linux Audio Session Handler (LASH) shared library files
 LASH is a session management system for JACK and ALSA audio
 applications on GNU/Linux.
 .
 Dynamic library used by the LASH system
Original-Maintainer: Guenter Geiger (Debian/GNU) <geiger@debian.org>
```

---

### Post by Bashing-om on 2012-09-09
ok ! on the right track...
a good status should read status: install ok installed
lets look at the output of
```
ls  /var/lib/dpkg/info/liblash*

```[INDENT]BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-09
In the terminal, right?

```
/var/lib/dpkg/info/liblash2.list    /var/lib/dpkg/info/liblash2.shlibs
/var/lib/dpkg/info/liblash2.postrm

/var/lib/dpkg/info/liblash2.md5sums:
B33E2d01

/var/lib/dpkg/info/liblash2.postinst:
B2BCEd01  D88CBd01
```

---

### Post by Bashing-om on 2012-09-09
fix:

```

sudo rm  /var/lib/dpkg/info/liblash2.list
sudo apt-get install liblash2 --reinstall

```

in the event you need/want that package, otherwise to un-install
```
sudo apt-get remove liblash2
```

run these and advise soonest ..and we do the cleanups.

[INDENT]BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-09
```
rm cannot remove '/var/lib/dpkg/info/liblash2.list': Read-only file system
```

---

### Post by Bashing-om on 2012-09-09
do not know why the file system is remounted as read only.... scary...see if we can fix it with terminal code:
```
sudo touch /forcefsck
sudo shutdown -r now

```

will check the filesystem and try and fix any errors when it boots back up.
this read only file system not related to our current updating problem (hummmmm I do not think).

[INDENT]BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-09
That didn't work. The disk check loaded to 70% and then didn't go anywhere. When I hit "C" to cancel, it froze, and I had to restart again.

---

### Post by Bashing-om on 2012-09-09
Not Good ! Could be your disk has bit the dust, (hope not) easier way to check this possibility ... if you can boot into your system ...use the disk utility (administration menu)
and run the smartmontools test to check the hard disk for errors. (full test).


[INDENT]awaiting advisement ==>BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-09
Huh?

---

### Post by Bashing-om on 2012-09-10
on 10.04
system->administration->disk utility
disk utility window-> select the hard disk in the left pane
in the ensuing window's upper right pane-> choose Smart Data (view SMART data and run self test)
next window -> choose self test  & Iiirc choose full test.


I have appointments in the am .. so will be several hours before I can respond.
perhaps others will pick this up ...I will check on your status soonest.

[INDENT]awaiting advisement ==>BDQ 
[/INDENT]

---

### Post by Olthar on 2012-09-10
Check finally complete. Everything is a-okay. No problems, and the disk is healthy. :)

---

### Post by Bashing-om on 2012-09-10
Great ! ...(that's a load off ) ...

As you do not at this time have a live install disk (to run file system fix) lets try one more time with the /forcefsck command as we have to get the file system repaired to get the partition mounted read and write ( ro = read only: to prevent further damage to the file structure).

  Be advised I am not comfortable attempting to boot into a damaged file system,,,This repair of the file system should be done from the live CD and or USB ..can not work on file system if operations files are open because we boot it up.


[INDENT]BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-10
I only understood about half of that...

---

### Post by Bashing-om on 2012-09-10
Olthar;
 Sorry for my poor communications skills.

I will try in simpler terms.

1. In regards to " rm can not remove .......read only file system"
      this error says the file system is damaged.
2. In order to restore the file system, a install CD is required.
3. We can not fix the update problem until the file system is restored.

questions;
    a. Do you have access to another computer ?
    b. Do you have a install cd ?
    c. is important data presently on your system backed up ?

4. I am not willing to do anything that might risk any damage to your file system


[INDENT]please advise ==>BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-10
A. Yes.
B. No.
C. Yes. I have all my personal files on an external harddrive.

---

### Post by Bashing-om on 2012-09-10
we will attempt to repair your file system. This method requires the use of the install cd.
Request you down load a .iso file and burn it as an image to cd.
Instructions are in this link:
[https://help.ubuntu.com/10.04/switching/C/installing-get.html](https://help.ubuntu.com/10.04/switching/C/installing-get.html)

advise when you are prepared to proceed

[INDENT]BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-10
I'll try doing that tomorrow.

---

### Post by Bashing-om on 2012-09-11
Good.

When you are booted up within the live cd ..please post the output of:
```

sudo fdisk -lu 
sudo parted -l

```
 to insure we are knowledgeable and working with the correct partitions.

The live cd environment (networking too) will be slower than with an installed system.
but I suggest you use this source until such time as your file system is repaired.

[INDENT]awaiting response <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-11
It might actually have to wait until tomorrow, unfortunately, as I don't have a blank CD available right now.

---

### Post by Bashing-om on 2012-09-11
not a problem .....at your convenience ...

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-13
Alright. That took *considerably* longer than I would have liked, but I finally have a blank CD. So, I'll do that all tomorrow morning.

---

### Post by Bashing-om on 2012-09-13
That is making progress ! One thing at a time. When you have a live cd made up ...we will get the file system back in order. That may even resolve the update issue. We will see. As i day, one thing at a time.

[INDENT]BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-14
So, I want to download 12.04, right?

---

### Post by Olthar on 2012-09-14
Yes? No?

---

### Post by Bashing-om on 2012-09-14
well... if you intend to remain with 10.04 ..I suggest the 10.04 .iso ..If you are going to upgrade to 12.04 ...then we will use the 12.04 .iso. I am fairly certain Gparted on the 12.04 .iso(burbed to cd) will have no problems looking/fixing your 10.04 file system.

[INDENT]BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-14
Yes. I want to upgrade. I would have done it already, but, well, my Update Manager isn't working. :P

---

### Post by Bashing-om on 2012-09-14
Olthar;

  Hey that is good too...I had some trepidation with leaving 10.04. But, once I had unity figured out .. I have not gone back. I discovered that unity works very well for me and the manner I use my computer. Surprisingly, I really like unity.

On Topic: Upgrade -> nothing to it. Save your work files, set bios to boot the burned cd,
boot the install cd ...run the "try ububtu" option to make sure everything works -networking, printer, graphics card ect ect....- If all appears working then choose install, follow the prompts, let the installer choose how to install (unless you have good reasons not too, as you may want a separate /home partition) and you are done ...

As you are going to go the upgrade route...no worry about fixing the 10.04 issues.

I will continue to watch this thread, to help in the event you have questions !

[INDENT]My regards <==BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-15
Alright, so I have the ISO file. So, what program do I use to put it on the disk?

---

### Post by Olthar on 2012-09-15
Help, please. D:

---

### Post by Bashing-om on 2012-09-15
I am here ... do you presently have the .iso file downloaded into your Downloads directory? 

double click on the .iso file ...insert the blank disk (CD - R does best) into the cd drive, choose "burn" image to disk. On the advanced tab: choose lowest burn speed & check the 'error checking' box. Then to the best of my remembrance ,choose "burn image to disk" ( this in ubuntu--from a windows environment with nero I do not remember--but it should be similar). You are to burn an image NOT copy data.

  If the need exist.. from my ubuntu system I will burn a disk and take exact notes on the process---- I have done it several times and never thought about the steps in the process---, but, is simple and straight forward.

[INDENT][INDENT]BDQ
[/INDENT][/INDENT]

---

### Post by Olthar on 2012-09-15
> **Bashing-om said:**
> I am here ... do you presently have the .iso file downloaded into your Downloads directory?
No. I got rid of that as I didn't think I'd need it. I just have the file sitting on my desktop.

---

### Post by Bashing-om on 2012-09-15
If it is the .iso file on your desktop (ubuntu) //the procedure from my last post should suffice.
double click the .iso file, choose burn, insert blank disk, slowest speed, burn as image ... I anticipate will get the job done.


[INDENT][INDENT]BDQ

[/INDENT][/INDENT]

---

### Post by Olthar on 2012-09-15
No, that just opens it up in WinRAR. :/

---

### Post by Bashing-om on 2012-09-15
*WinRAR* is a Windows data compression tool that focuses on the RAR and ZIP data compression formats for all Windows users.

as such in windows I am not to much help ...A long time past I used nero as a utility to burn to disk. //Now-a-days I do not know what utilities are on windows.

 I am regretful that I am not much help. I have not had a windows system in years.

Seems like the clicking of the file should work. See this link:
[http://windowsteamblog.com/windows/b/windowsexperience/archive/2009/04/13/burn-iso-images-natively-in-windows-7.aspx](http://windowsteamblog.com/windows/b/windowsexperience/archive/2009/04/13/burn-iso-images-natively-in-windows-7.aspx)

In the event that you are not using a windows operating system to burn this .iso to cd disk as an image ..what system are you utilizing ?
[INDENT]BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-15
> **Bashing-om said:**
> In the event that you are not using a windows operating system to burn this .iso to cd disk as an image ..what system are you utilizing ?
I'm using 10.04 Ubuntu... :|

---

### Post by Bashing-om on 2012-09-15
ok ...10.04 ubuntu... I am downloading an.iso via 10.04 and will burn the image ,,,will take careful notes and advise you... I have a very slow connection on the net at this time and will take 2 hours to complete the download,,
I will post back with details.
[INDENT]BDQ

[/INDENT]

---

### Post by Olthar on 2012-09-15
Okay.

---

### Post by Bashing-om on 2012-09-16
ok..got it done: here is the detailed process for using 10.04 ubuntu to burn the .iso image to the cd disk:

1. right click on the .iso icon, choose from the pop up menu ->write to disk
    write to disk window opens.
2. Insert blank cd R disk into disk drive ->window:blank CD - R Disk opens ->choose cancel
     returns to write to disk window.
3. In the reopened write to disk window choose properties:
4. Properties of HL-DT-ST DVD-RAM GH22NE (that may be different on your system)
    choose in maximum speed -> 16.0x (cd)
    insure "burn proof (decrease risk of failures) is checked
    leave Temporary files set to the default location
    click close on this window at this time.
5. click burn ===> .iso is burning as image to cd
6. notification that copy is completed ==> click close.

done.

one may now check the disk integrity with the md5sum and/or boot the new install cd holding the shift key down enables the boot options menu. In the boot options menu choose to check the disk for defects. (remember to set bios to boot cd drive as first priority)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)


I will await developments ==>BDQ

---

### Post by Olthar on 2012-09-16
> **Bashing-om said:**
> 1. right click on the .iso icon, choose from the pop up menu ->_**write to disk**_
I don't have that.

---

### Post by Bashing-om on 2012-09-16
Olthar;

 Surely you must have that option... it is located near the end of the list.
If you have a .iso file and you right click on it ...the option in ubuntu 10.04.4 is there (I just verified it ..I promise !) 
 Now, if it is a .iso .tor file ..then the torrent file must be written as a .iso file and then written to cd.

---

### Post by Olthar on 2012-09-16
What, do you think I'm lying? What possible reason would I have to do that? :|
I'm telling you the truth. There is no "write to disk" option.

---

### Post by Bashing-om on 2012-09-16
I did not mean to imply that ... I do not understand why you do not have that option.

I have booted up 10.04, I have downloaded the 12.04 as an .iso, I have burned the .iso to a cd with the 10.04 install...I do have that "write to disk" option with the "right click".

My thoughts are that you are:
  a. You are not using 10.04 ubuntu
  b. You have downloaded a torrent file (which is fine, just have to convert it to the .iso imaging file)

 I remain diligent to get you up stable on ubuntu, whatever it may take.
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Olthar on 2012-09-16
I am definitely using 10.04, and it is definitely not a torrent file. :/

---

### Post by Bashing-om on 2012-09-16
All right ...'nother approach:

See if the Brasero package is installed.
applications->Sound & Video->Brasero Disk Burner ??????


Is it there ?

[INDENT][INDENT][INDENT]BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by Olthar on 2012-09-16
No, and before you ask, I did try installing it with the Software Center. Long story short, liblash2 apparently affects more than just the Update Manager. :(

---

### Post by Bashing-om on 2012-09-16
not really surprised. 
ok is the disk drive writable at this time ?
If we can, run these one line at a time to fix dpkg's config files:
```

1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info
8. sudo apt-get clean
9. sudo apt-get autoremove
10. sudo apt-get update

```

Try these commands and tell me update works (please)...BDQ

---

### Post by Olthar on 2012-09-16
I can't edit the file. It's read only.

---

### Post by Bashing-om on 2012-09-17
we are back where we were... got to come up with a way to burn a install cd or usb. Then we can either fix the 10.04 or, as you desire, upgrade to 12.04.

  There is no other option at this time.
[INDENT][INDENT]BDQ
[/INDENT][/INDENT]

---

### Post by Olthar on 2012-09-17
Alright. So how do I do that? :/

---

### Post by Bashing-om on 2012-09-17
The only suggestion I have now is to use another computer, d/l the .iso again, and on the other computer-> burn the install image.

patience is a virtue ...and you are very virtuous //BDQ

---

### Post by Olthar on 2012-09-17
Seriously? That's not what I wanted to hear. :/

---

### Post by Bashing-om on 2012-09-17
Yeah, It's frustrating .... but there is no getting around the fact that a live install media is required, either a cd or a usb thumb drive.

  Reasoning:  Your 10.04 is reaching End-of-Life ....upgrading to 12.04 is the solution.
                          upgrading to 12.04 from 10.04 requires a clean install.
thus: we have to have a install means. 

[INDENT][INDENT]BDQ

[/INDENT][/INDENT]

---

### Post by Olthar on 2012-09-21
Hey, sorry I haven't said anything in a while. I've been really busy lately, and I just don't have time to upgrade to a new operating system right now. Though, I should be able to do it sometime next week. I'll make another post when I'm ready.

---

### Post by Bashing-om on 2012-09-21
Time is not a problem on my account. We will finish this up when you are ready. I will continue to monitor this thread. We should finish it up in this thread for continuity.

[INDENT][INDENT]regards <==BDQ

[/INDENT][/INDENT]

---

