---
title: "Xubuntu's Synaptic can't autenticate Sudo's update"
date: 2010-03-02
forum: General Help
---

### Post by Suburbia on 2010-03-02
Hello:

I recently installed Xubuntu (9.10) in my computer, but... I have been having intermitent hard disk problems, and so I decided to google a little and after reading this:

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

I did use Synaptic to search for smartmontools and then install it.

Synaptic complained that it couldn't autenticate the packet, but I figured this was happening because... this is not an application supported by Canonical? :-? I clicked and installed the packet (well, in fact, I *think* it has installed two applications, not just one).

Then later, I saw one of those arrows at the top right of the screen, and clicked it to install updates. Synaptic told me to update SUDO. Hmm... serious. And then even more: it told me that it couldn't autenticate it :o I stopped the installation and registered at these forums.

And more: before posting, I tried to reproduce the "error" (and again, stop before installing the "suspicious" SUDO update) but Synaptic now autenticated it troubleless and installed it (!!!).

Well, now I have a LOT of questions:

1. Where do I place this post?. Security?. Hardware problems?. Update and installation? (Linux noobiness?)
2. Any more advice with my hard disk?. I've read somewhere that an application called "fsck" or something could be of any help?
3. What may have happened with Synaptic?. Why wouldn't it autenticate a SUDO update?
4. Have I done something wrong?. Something unrepairable?
5. Can I trust the SUDO version that now I have installed in my system?
6. How could I check what has Synaptic exactly installed?. Is there any log file anywhere in my system?

Well, not bad for a first post... do you think you can help me? 8-[

---

### Post by plucky on 2010-03-02
Welcome to Ubuntu Forums.


> 1. Where do I place this post?. Security?. Hardware problems?. Update and installation? (Linux noobiness?)

When in doubt **General Help** is a good place to post.If it is in the wrong place,the mods will move it.


> 2. Any more advice with my hard disk?. I've read somewhere that an application called "fsck" or something could be of any help?

Fsck is a file system check which will run automatically after the partition have been mounted a certain number of times.It is run at boot time.
If you suspect a hard disk problem,it might be a good idea to go the the disk drive manufacturers' website and download their diagnostic tools.
Or get yourself a copy of the **Ultimate Boot CD** which has a number of diagnostic tools on it.

> 3. What may have happened with Synaptic?. Why wouldn't it autenticate a SUDO update?

Open a terminal window **Applications > Accessories > Terminal** and run ```
sudo apt-get update
``` Input your password,which won't be echoed,then run ```
sudo apt-get upgrade
```
Post any errors to the forum.
Don't bother about the sudo problem as there was an update last Saturday.Hopefully the two commands above will fix the authentication problem.
> 4. Have I done something wrong?. Something unrepairable?
Sometimes things break,most things are repairable.
> 6. How could I check what has Synaptic exactly installed?. Is there any log file anywhere in my system?


In Synaptic you can go to **File > History** to find out what has been installed in Synaptic.

Good Luck

Hope this helps.

---

### Post by Suburbia on 2010-03-04
First of all, thanks for the help.

Regarding my problem with sudo, I checked the File>History menu in Synaptic, and there was info about all my updates. Very helpful, to start with.

Then I googled and read a lot, and found sudo's homepage:

[www.sudo.ws]("http://ubuntuforums.org/www.sudo.ws")

Where I confirmed the recent upgrade of sudo.

Reading and reading and reading more, I found about these commands, which have also helped me:

```
apt-cache policy sudo
```Which resulted in this:

sudo:
  Instalados: 1.7.0-1ubuntu2.1
  Candidato: 1.7.0-1ubuntu2.1
  Tabla de versión:
 *** 1.7.0-1ubuntu2.1 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
        100 /var/lib/dpkg/status
     1.7.0-1ubuntu2 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Packages

And also:

```
apt-cache policy smartmontools
```smartmontools:
  Instalados: 5.38-3ubuntu2
  Candidato: 5.38-3ubuntu2
  Tabla de versión:
 *** 5.38-3ubuntu2 0
        500 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status

If I'm not wrong, this confirms that I (well, Ubuntu) have downloaded the packet upgrades from the correct sources (notice spanish is my mother tongue...). By the way, is there a more intuitive way for doing this? :?

Also while in Synaptic, right-clicking on the packets and then selecting "Properties" has been very helpful; this way I can know which files have been installed (and where).

Ahem, some more questions:

1. I've read that the list of repositories should be in a "source.list" file somewhere in my system, but I can't seem to find it (?).

2. I ran the commands that plucky suggested me (apt-get update and apt-get upgrade), and... how is it that Synaptic tries to update a different numbers of packets than apt-get (Synaptic 18, apt-get 12)?. I thought Synaptic is a kind of... "graphical interface?" of apt-get (and so they should upgrade the same number of packets).

Regarding my problem with my HD... well, it is still working, and the UltimateBootCD web seemed to have loads of information (most of it for Windows users...). Well, when I'll digest the info (and if my HD still works) more questions will come.

---

### Post by plucky on 2010-03-04
> 1. I've read that the list of repositories should be in a "source.list" file somewhere in my system, but I can't seem to find it (?).



From a terminal ```
cat /etc/apt/sources.list
``` will show you what your sources.list contains.


> 
2. I ran the commands that plucky suggested me (apt-get update and apt-get upgrade), and... how is it that Synaptic tries to update a different numbers of packets than apt-get (Synaptic 18, apt-get 12)?. I thought Synaptic is a kind of... "graphical interface?" of apt-get (and so they should upgrade the same number of packets).

apt-get,aptitude,synaptic,software centre are all front ends to **dpkg** which actually installs the packages.

Use ```
man apt-get
man dpkg
``` to find out what the apt-get and dpkg commands do.

Good Luck

---

### Post by Suburbia on 2010-03-13
Hello; as you can see, my hard disk is still working.

I've used the smartctl tool to get some information about my hard disk, and then I've conducted a short and a long test on my hard drive.

There haven't been any alarming results, unless you consider this hard disk working at 52º Celsius (at some point in his past lifetime, if the log is accurate) should be something alarming, or an errors count of 101 (the log only saves data about the last five, which all occurred while reading sector 1...) alarming.

I must mention that I changed my operative system to Xubuntu because some update in my Windows XP didn't work well, and it was taking 10 minutes to start the system. My suspect is that this may have something to do with the high count of errors, but still, I don't like being overconfident, and I've tried to run fsck, unsuccessfully.

If I understand things correctly, fsck should work as chkdsk worked in MS-DOS, and it should check for bad sectors and mark them as bad, not to use them to storage data anymore. Am I correct?.

Trying to run fsck reported the following errors:

```
¡¡WARNING!! Executing e2fsck in a mounted filesystem while it is mounted may cause SERIOUS damage to the filesystem.

Would you like to continue?
```To which of course, I replied NO. This happens if I try fsck with /dev/sda1, where my starting partition (how do you call this?) is located.

If I try it with /dev/sda2 (see, the installing disk created an extended partition), then I get the message:

```
fsck.ext2: Attempt to read block from filesystem resulted in short while trying to open /dev/sda2

May this be a cero lenght partition?.
```(Note that I've translated part of these messages from spanish, my mother tongue. Sorry for any innaccuracies). I'm getting the feeling that I'm very close to do... something very risky to my filesystem. I better ask someone more seasoned.

Well, do you think guys you can help me?:

1. Is fsck the tool that I must use for checking for bad sectors and then marking them as unusable?. Which one should I use, then?.

2. How do I use fsck?. I think it should run automatically on start after a bad shutdown, but I find this method would be a little rude...

3. I've been reading some of the man pages for all of these tools (I mean it!), but I'd like to read them more thoroughly; where are they located in my hd?. Can't I see them with my pdf reader?.

Well, thanks in advance for any help.

---

### Post by srs5694 on 2010-03-13
> **Suburbia said:**
> If I understand things correctly, fsck should work as chkdsk worked in MS-DOS, and it should check for bad sectors and mark them as bad, not to use them to storage data anymore. Am I correct?.

fsck is more about checking the integrity of the filesystem data than about finding bad blocks, although there is a way to use it to scan for bad blocks: Use the e2fsck utility (the version that's specific to the ext2/ext3/ext4 filesystems, assuming that's what you're using) and its -c option. Type "man e2fsck" and page down to the description of "-c" for details.

> Trying to run fsck reported the following errors:

```
¡¡WARNING!! Executing e2fsck in a mounted filesystem while it is mounted may cause SERIOUS damage to the filesystem.

Would you like to continue?
```To which of course, I replied NO. This happens if I try fsck with /dev/sda1, where my starting partition (how do you call this?) is located.

To check any mounted filesystem, it's safest to unmount it first, or at least re-mount it read-only. If your installation has just one filesystem (as most new Ubuntu users seem to do), or if you want to check your root filesystem, your best bet is to shut down and boot a Linux emergency system to do the job. The Ubuntu install disc might do it, but I generally use [PartedMagic](http://www.partedmagic.com) or [System Rescue Cd](http://www.sysresccd.org) for this sort of thing. These are both Linux emergency systems with copies of fsck and lots of other common system recovery and maintenance tools.

> If I try it with /dev/sda2 (see, the installing disk created an extended partition), then I get the message:

```
fsck.ext2: Attempt to read block from filesystem resulted in short while trying to open /dev/sda2

May this be a cero lenght partition?.
```

If /dev/sda2 is an extended partition, then you shouldn't use fsck on it. The Master Boot Record (MBR) partitioning scheme used on most Linux systems includes a distinction between primary partitions (numbered 1-4), extended partitions (a special type of primary partition that holds the next type), and logical partitions (numbered 5 and up). This is a workaround for a very very old design limitation: Namely, room for only four partition definitions in the main MBR partition table. A single extended partition serves as a placeholder for multiple logical partitions, so you don't use filesystem maintenance tools on extended partitions, although you might use such tools on logical partitions, depending on what *they* hold.

If you continue to have problems relating to this, you might want to post the output of the "fdisk -l" command (you may need to use sudo to get this to work), which shows your partition table.

> 2. How do I use fsck?. I think it should run automatically on start after a bad shutdown, but I find this method would be a little rude...

Actually, it does run automatically after a bad shutdown. Most Linux filesystems have a "journal," though, which is basically a way to speed up the run of fsck after a power failure or other bad shutdown.

> 3. I've been reading some of the man pages for all of these tools (I mean it!), but I'd like to read them more thoroughly; where are they located in my hd?. Can't I see them with my pdf reader?.

Most man pages are in the /usr/share/man directory tree, but there are other possible locations. (Type "echo $MANPATH" to see all the possibilities.) You can tell which specific subdirectory by noting the number associated with the topic when you read the man page, as in:

```

FSCK(8)                      MAINTENANCE COMMANDS                      FSCK(8)

```

The "8" means it's in man section 8, hence /usr/share/man/man8.

There are various conversion utilities that might be of use if you'd like to read in another format. One is xman, which is an X-based man page reader. Type "xman" at a shell prompt to launch it. It is, however, a very old program and doesn't seem to have a print option.

If you want to read on paper, try man2html or [man2pdf.](http://www.aasan.org/download/man2pdf) The former is available in the Ubuntu repositories, so you can install it via apt-get or Synaptic; it converts man pages to HTML so you can read in a Web browser, and print the output if you like. The latter is a shell script that I found in a Web search; however, it relies on several tools that you may or may not have installed. One is called bz2cat, which I can't find on my Ubuntu system. When I replaced "bz2cat" with "bzcat" in the script, though, it started working. To use it, you'll need to make it executable (type "chmod a+x man2pdf") and then either copy it to a suitable program file directory (I suggest /usr/local/bin) or type its complete path whenever you want to use it.

---

### Post by Suburbia on 2010-03-14
> **srs5694 said:**
> If /dev/sda2 is an extended partition, then you shouldn't use fsck on it. The Master Boot Record (MBR) partitioning scheme used on most Linux systems includes a distinction between primary partitions (numbered 1-4), extended partitions (a special type of primary partition that holds the next type), and logical partitions (numbered 5 and up). This is a workaround for a very very old design limitation: Namely, room for only four partition definitions in the main MBR partition table. A single extended partition serves as a placeholder for multiple logical partitions, so you don't use filesystem maintenance tools on extended partitions, although you might use such tools on logical partitions, depending on what *they* hold.

If you continue to have problems relating to this, you might want to post the output of the "fdisk -l" command (you may need to use sudo to get this to work), which shows your partition table.

I thought I'd post the result of the fdisk -l command in my system:

Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pista, 7296 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xfb72fb72

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        7113    57135141   83  Linux
/dev/sda2            7114        7296     1469947+   5  Extendida
/dev/sda5            7114        7296     1469916   82  Linux swap / Solaris

If I've understood your explanation well, MBR is in /dev/sda1 (the one marked with the asterisk), /dev/sda2 is an extended (a special type of primary partition) partition wich can sustain (physically) many logical partitions, but in this case only one, /dev/sda5, which serves as swap (extra memory for the system in the hd). Am I correct?.

> Most man pages are in the /usr/share/man directory tree, but there are other possible locations. (Type "echo $MANPATH" to see all the possibilities.)I've located the files in my HD, but typing "echo $MANPATH" didn't give any results but a blank line. Hmm... is this bad?.

Thanks for the help!

---

### Post by Suburbia on 2010-03-23
Hello, I can't remember where, but some place in this forum I read that one should mark a thread as "solved" when... well, when it is solved.

Despite how I named it, this tread has had two main subjects:

1. Mistrust when Synaptic didn't seem to autenticate an update of the sudo program.

2. Looking for help to test and repair my hard disk.

Sorry for the confusing thread tittle.

The first one was quickly resolved; it looks like Synaptic doesn't tolerate well updates from a virtual console/terminal program; I can see the red arrow in my top panel now (indicating me that I should install important updates), despite the fact that I've installed those updates using the terminal window (you know, apt-get upgrade).

Regarding the second one, I downloaded and burned the Parted Magic 4.8 CD, and tested my hard disk through the smartctl long self-test and the e2fsck -c -c /dev/hda1 command (this last took loooong).

It doesn't seem like there's any bad sector in the disk (the e2fsck didn't report any after completion); but the smartctl tool reported that there has been 101 "UDMA CRC error count", which is exactly the total number of errors accounted at the disk's log (a pity this hard disk's log only stores information about the last five errors which, coincidentally, are all ICRC).

This seems to be some problem with the cable that transmits the data (I'm not an expert in hard disks), but I don't know where is this cable, and I don't know how would I fix something like that. I've taken the hard disk out of the laptop and put it in place again; hoping that a better contact in the... "pins?" would help.

According to the smartctl reports, the last error happened 343 hours ago (and that's a lot, I don't use this computer 24 hours a day). I have all my important data well stored, and this tread seems to be deviating from it's initial subject. I'm about to mark it as "solved".

The last questions, I think:

1. How can I tell if the e2fsck command found (and didn't report to me) any bad sector?

2. Can any of you tell me more about this "UDMA CRC error count" or where's this cable that I think is (was) causing the trouble?

3. Has anyone anything else to add/advice?

Thanks in advance.

---

### Post by Suburbia on 2010-04-02
Well, I think this thread can be marked as "solved" yet.

Special thanks to plucky and srs5694; having someone you can ask to really eases the learning process.

):P

---

