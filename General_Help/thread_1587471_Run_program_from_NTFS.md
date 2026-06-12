---
title: "Run program from NTFS"
date: 2010-10-03
forum: General Help
---

### Post by Warthaug on 2010-10-03
I a setting up a dual-boot system.  The two OS's (ubunt ad win7) are on smaller partitions, with a shared NTSF partition for data and whatnot.

In ubuntu, the NTSF partition has been mounted at /media/Data/

I am running ubuntu 10.04, 64bit


I was hoping I could install a few programs to the NTSF partition, and run them from there.  However, when I do so I cannot run them - I get a permissions error (even if I run using sudo).  I cannot change the ownership from root, so I cannot overcome this problem.

Is it possible to run programs from this shared folder, or is it an impossibility?

Thanx

Bryan

---

### Post by btindie on 2010-10-03
What's the output of ```
sudo mount
```
 
If you remount it with exec permissions then it may work
```
sudo mount -o remount,exec /media/Data
```
 
Is there an entry in /etc/fstab for the partition? If so then add *exec* to the list of mount flags.

---

### Post by coffeecat on 2010-10-03
> **Warthaug said:**
> Is it possible to run programs from this shared folder, or is it an impossibility?

NTFS does not support Linux/Unix permissions which you need for applications files. It *might* be possible to run a simple bash script or a simple binary from an NTFS partition seeing that all files on NTFS are seen as executable in Linux. But I wouldn't try it. :-s

Most applications files go in /usr and configuration files go in /etc with your personal configurations in /home. All of these folders **must** be on a Linux filesystem. Which means you cannot run Linux applications from a Microsoft fileystem.

---

### Post by srs5694 on 2010-10-03
Coffeecat's answer is too extreme; btindie is correct that mount options, including the ability to run programs from an NTFS partition, can be controlled by mount options. I would add that a suitable execute bit must be set on all files. This detail can be controlled via the umask and/or fmask mount options, so you might need to adjust those.

That said, coffeecat is correct that Linux binaries typically go in specific directories, such as /bin, /sbin, and certain subdirectories of /usr. You *can* change your PATH or run programs directly from elsewhere, but unless you have a good reason to do so and know what you're doing, it's safest to stick with the default configuration. Furthermore, there's little or no real reason to put Linux binaries on a Windows-accessible partition. Windows can't run them, after all, so there's not much point in putting them there. The only plausible reason I can think of to do this would be for cross-platform files, like certain shell scripts or Java applications. Most of these programs can be run without setting the executable bit, although you may need to explicitly call the support program, as in "bash /path/to/ntfs/someshell.sh" to run a bash script. I suppose you could save yourself a little maintenance time by sharing such programs in this way, but the savings would be tiny unless you run dozens of such programs.

If you need more advice, I suggest you post more details, such as what types of programs you want to run in this way (binaries, Java programs, bash scripts, etc.), why you want to put them on NTFS, what your existing /etc/fstab entry looks like (if you've got one), and what permissions the files have now (as revelead by "ls -l /path/to/ntfs/programname", for instance, substituting an appropriate program filename and path).

---

### Post by dcstar on 2010-10-04
> **srs5694 said:**
> **Coffeecat's answer is too extreme**; btindie is correct that mount options, including the ability to run programs from an NTFS partition, can be controlled by mount options.
........

He is 100% correct.

Linux programs are specifically designed to use Linux system folders on filesystems with full support of all Linux filesystem features. NTFS does **not** meet this requirement. NTFS does not even support file names which are legal in Linux (like anything starting with "."), guess what happens when a Linux program tries to create/access a hidden folder/file on a NTFS filesystem?

---

### Post by coffeecat on 2010-10-04
> **srs5694 said:**
> Coffeecat's answer is too extreme

> **dcstar said:**
> He is 100% correct.

Ho hum. I certainly didn't want to be the cause of an argument, neither do I wish to perpetuate one, but permit me to observe that if I appeared to be too extreme, it was perhaps because I was over-simplifying, and I don't believe I've ever been 100% correct. I am, after all, a mere mortal being. :wink:

If I appeared to be dogmatic with my emboldened 'must', I apologise. I was thinking of the subtle differences in r-w-x permissions between various files in both /home and /usr. How much that would affect various apps if you tried to run them from a NTFS filesystem I don't know, and I don't care to waste time trying to find out. Add that to the complicated way apps liberally sprinkle their consituent files throughout the filesystem I assumed it would be a nightmare, and probably an unproductive nightmare, trying to get most apps running from NTFS. And none of us has yet mentioned /lib. What about all the shared libraries an application might need? It would be more than a nightmare trying to set up all the links necessary.

Before anyone picks me up for this:

[quote="coffeecat"]seeing that all files on NTFS are seen as executable in Linux[/quote]

I was thinking of the way NTFS filesystems are automounted by Ubuntu, or the commonly recommended options for fstab, in both of which cases files on NTFS are seen as executable. As I am almost daily reminded when I double-click on an ordinary text file saved in NTFS. I know about the nonexec option but that would be the opposite of what the OP wants.

By the way, NTFS will allow you to create file/folder names with a leading dot. They will be cheerfully displayed in Windows and just as cheerfully hidden in Ubuntu. How that would affect running apps I don't know and again am not disposed to find out.

Once again, apologies for seeming dogmatic, but perhaps srs5694, dcstar and I might wish to find common ground and advise the OP that their proposed idea is, for pragmatic reasons, not a good one. Agreed? :)

---

### Post by Warthaug on 2010-10-04
My fstab:
```
UUID=62D67BA0D67B7361 /media/Data ntfs-3g users 0 0
UUID=00dbf9f3-42ef-43ea-9a73-f2cbc9c55a15 / ext4 defaults 0 1
UUID=207e8955-d735-4f23-b523-46b17c74eec8 swap swap sw 0 0
```

The top entry is the data drive I am trying to execute from.

The reason is simple - some of the software we use is propriatary, and requires 3rd party activation.  Meaning any time we upgrade ubuntu (i.e. wipe the drive) we need the manufacturer to re-active the software.  Since I try to keep up-to-date with ubuntu releases, that means every 6 months.  I was hoping that by installing it on the NTSF partition I could avoid this issue.

Sounds like it may be more trouble than it is worth....life would be so much simpler if work didn't dictate that I keep windows on my computer...

Bryan

---

### Post by Mark Phelps on 2010-10-04
IF what you're talking about is MS checking activation of their products, even if you COULD do what you're asking, I doubt that would solve the activation "problem".

While MS doesn't reveal all the nitty details of their activation logic, it does appear to be tied to information contained in the drive to which MS Windows is installed.  So, if you're using the same drive for Ubuntu, every time you wipe and reformat and reinstall to that drive, some hidden information gets changed.

MS Windows is going to detect that change when it later boots, and if the change is severe enough (MS won't really come clean on what constitutes "severe enough"), it will deactivate the products.

---

### Post by srs5694 on 2010-10-04
> **dcstar said:**
> [quote=srs5694]**Coffeecat's answer is too extreme**; btindie is correct that mount  options, including the ability to run programs from an NTFS partition,  can be controlled by mount options.He is 100% correct.

Linux programs are specifically designed to use Linux system folders on filesystems with full support of all Linux filesystem features. NTFS does **not** meet this requirement. NTFS does not even support file names which are legal in Linux (like anything starting with "."), guess what happens when a Linux program tries to create/access a hidden folder/file on a NTFS filesystem?[/QUOTE]

This debate may hinge on the question of what is meant by "program." I interpreted it to mean a single executable file. You seem to be interpreting "program" much more broadly, including not only the program, but support files in the system (libraries, configuration files, etc.) and maybe even user data files.

To illustrate the veracity of my own claims given my interpretation of "program," consider this:

```

$ df -h /other/shared/
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              12G  6.2G  5.4G  54% /other/shared
$ sudo blkid /dev/sdb5
/dev/sdb5: UUID="E4867E6C867E3F5C" LABEL="XP Programs" TYPE="ntfs" 

```The preceding commands illustrate that /other/shared is an NTFS volume. Now, I'll copy a Linux binary program to it and execute that program *from NTFS:*

```

$ cp /usr/sbin/gdisk /other/shared/
$ sudo /other/shared/gdisk /dev/sda
GPT fdisk (gdisk) version 0.6.11

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************


Command (? for help): q

```The program ran fine, although I didn't do anything with it. Now, to the point about dot files:

```

$ touch /other/shared/.foo
$ ls -lh /other/shared/.foo
-rwxrwxrwx 1 rodsmith root 0 2010-10-04 13:56 /other/shared/.foo*

```Clearly, the dot file exists on NTFS. I didn't reboot into Windows to see how it would react, but it's certainly possible to create dot files on NTFS from Linux.

When looking beyond running a simple single binary from NTFS, you could reasonably say that NTFS is insufficient to host program binaries *and certain support files for specific programs.[/url] Support file needs vary from one program to another, though, so saying that it won't work in an absolute manner is simply wrong, as I've just illustrated. Under a broader interpretation of the meaning of "program," details of [I]what* program, as well as what specific files for that program, should be installed to NTFS become critically important before an answer can be given.

Ultimately, it gets down to what the OP means, which wasn't entirely clear until a later message....

[quote=Warthaug]The reason is simple - some of the software we use is propriatary, and  requires 3rd party activation.  Meaning any time we upgrade ubuntu (i.e.  wipe the drive) we need the manufacturer to re-active the software.   Since I try to keep up-to-date with ubuntu releases, that means every 6  months.  I was hoping that by installing it on the NTSF partition I  could avoid this issue.[/quote]

There may be a fairly simple in-Linux solution to the problem, but the details depend on the software, how it's installed, where it stores its activation information, and what types of anti-piracy checks it performs. Specifically:


[list]
[*]If the software installs itself entirely to /opt, as is common for third-party software, you might be able to achieve your goals by splitting /opt off into its own partition.
[*]Alternatively, instead of putting /opt on its own partition, you could back it up and then restore it after you've done your system wipe and re-installation.
[*]If the software is installed via a Debian package to /opt, its installation information will be in a database that will be wiped out when you re-install Ubuntu from scratch. This might not be a big problem unless you need to upgrade it later. If the software installs to /opt via a tarball or installer utility, this won't be a problem after an Ubuntu re-installation.
[*]If the software stores activation information in a file in /opt, /etc, or some other location, you might be able to back up and restore that file. Of course, if it were that easy, the software's publisher probably wouldn't want you to know it, since they're clearly afraid of piracy, and transferring a single activation file would make it easy for pirates.
[*]If the software checks something about the system as part of an anti-piracy system, it might not work after a complete OS upgrade even if you keep all its files intact, since the OS might change enough for the software to refuse to run.
[/list]
Overall, your best bet is to call the publisher, explain the situation, and hope they're reasonable enough to offer help rather than assume you've got a peg leg, an eye patch, and a parrot on your shoulder.

Failing that, if the software installs to /opt, I'd try either backing it up and restoring it after an upgrade or putting /opt on its own partition; and I'd also have a look through /etc to find any configuration files for the software that might be backed up and restored.

---

### Post by Warthaug on 2010-10-05
> **Mark Phelps said:**
> IF what you're talking about is MS checking activation of their products, even if you COULD do what you're asking, I doubt that would solve the activation "problem".

Nope.  Its a high-end image processing/microscope controlling program.  Every time you start it, it accesses the companies licensing server to check your subscription.  We are loosing the licensing key whenever we replace ubuntu.  The manufacturer said that we should be able to solve this problem by installing the program to a separate partition that doesn't get wiped during upgrade.  My problem is that, due to "the rulez", I cannot alter the partitions on my laptop.  So the only partition available to me is the shared windows/ubuntu "data" partition...

Bryan

---

### Post by Warthaug on 2010-10-05
> **srs5694 said:**
> This debate may hinge on the question of what is meant by "program." I interpreted it to mean a single executable file. You seem to be interpreting "program" much more broadly, including not only the program, but support files in the system (libraries, configuration files, etc.) and maybe even user data files.

The program itself is a fairly large one, consisting of over 2000 separate files.  The entirety of the program installs into its own folder - nothing in opt, bin, home, or any other system folder.  Simply backing it up doesn't work - its encryption is somehow keyed in order to prevent that sort of "copying" (yes, I've tried).  As I mentioned in my last post, the manufacturer stated that putting it on a partition separate from the OS should prevent these problems -- but in the case of my laptop, I'm not allowed to make a new one - so all I have is the NTFS.

Sounds like its a lost cause.

Bryan

---

### Post by coffeecat on 2010-10-05
> **Warthaug said:**
>   As I mentioned in my last post, the manufacturer stated that putting it on a partition separate from the OS should prevent these problems -- but in the case of my laptop, I'm not allowed to make a new one - so all I have is the NTFS.

Sounds like its a lost cause.


Perhaps not. Could you elaborate on the laptop not allowing you to make a new partition? Are you running foul of the maximum allowable 4 primary partitions? Perhaps removing your NTFS data partition and the present Linux partition(s) would allow you to create an extended partition in the space and have your NTFS data partition, Linux partitions and the separate application partition on logicals within the extended.

What's the output of...

```
sudo fdisk -lu
```

---

### Post by srs5694 on 2010-10-05
I interpreted Warthaug's comment to mean that his employer won't permit changing the partitions. If that's the case, then I'd suggest trying to make that change at the next OS re-installation; the employer might be willing to accept such a change as part of the OS re-installation, since partitioning is often required for this activity anyhow. Create a small separate partition at that time, install the software, re-activate it once, and keep the partition in place thereafter.

Alternatively, you could use a loopback mount. That is, create an empty file of a suitable size, put a filesystem on it, mount it at the desired location using the loopback interface, and install the software on it. Something like this entry in /etc/fstab should automount it thereafter (I'm putting it in /opt because that's the standard Linux location for third-party software, but it could be anywhere):

```

/usr/share/opt.img  /opt  ext3  loop  0 0

```

You can then back up the file (/usr/share/opt.img) and, when you re-install Ubuntu, restore it and the /etc/fstab entry.

Another option that's conceptually similar is to store the software on an external device. If the software is small enough and speed isn't important, a USB flash drive would work fine. If the software requires gobs of space and/or if a USB interface isn't fast enough, you might need an eSATA hard drive. Either way, you just create an /etc/fstab entry, mount it, install the software, and then keep it unplugged when you re-install Ubuntu and then re-create the /etc/fstab entry afterwards. (You could plug the drive in when re-installing, but there's a tiny risk that you'll accidentally erase the disk's contents if you do this.)

---

### Post by Warthaug on 2010-10-06
> **coffeecat said:**
> Perhaps not. Could you elaborate on the laptop not allowing you to make a new partition? Are you running foul of the maximum allowable 4 primary partitions?
Nope, I'm running afoul of the our IT guys know less about computers than your average 7-year old, and the institute lets them set computer policy problem.

An extended partition would be needed in this case, policy issues aside.

Brya

---

### Post by Warthaug on 2010-10-06
> **srs5694 said:**
> Another option that's conceptually similar is to store the software on an external device. If the software is small enough and speed isn't important, a USB flash drive would work fine. If the software requires gobs of space and/or if a USB interface isn't fast enough, you might need an eSATA hard drive.
This may work - I'll give it  a go.

I'm also considering the f*ck the IT guys and do what I want route...

Bryan

---

### Post by srs5694 on 2010-10-06
Here's another idea: If the IT policies forbid creating new *partitions,* you could do an LVM installation, using a single partition for the LVM and as many logical volumes as you like inside that partition, including one for the proprietary software. That way you'd at least be within the letter of the law, as it were. You'd have to be careful to use GRUB 2, though; the older GRUB Legacy can't boot a kernel that stored inside an LVM, so it needs a separate partition for /boot. The last version or two of Ubuntu use GRUB 2, so in theory this shouldn't be a problem. I've never tried booting a kernel from inside an LVM, though, so I can't say from experience that it'll work.

---

### Post by Warthaug on 2010-10-06
LVM = ???

Problem resolved itself - an ext4 partition magically appeared - I don't know from whence it came, nor whom brought it, but its there now...

...that's my story and I'm sticking with it.  IT can KMY.

Bryan

---

### Post by srs5694 on 2010-10-06
LVM = [Logical Volume Manager](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) (Link is an arbitrary one from a Google search.) It's a way to allocate disk space that's more complex, but also much more flexible, than traditional partitions.

---

