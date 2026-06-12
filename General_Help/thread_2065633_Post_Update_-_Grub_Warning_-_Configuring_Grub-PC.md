---
title: "Post Update - Grub Warning - Configuring Grub-PC"
date: 2012-10-02
forum: General Help
---

### Post by Ace..... on 2012-10-02
I have just clicked to install the latest updates, and during this process (that normally proceeds flawlessly) the above stated grub warning popped up.

I can't copy the help statement cos unfairly, it won't let me.
However it effectively says that:
*****
The grub loader was previously installed to a disk that is no longer present, or whose unique identifier has changed.
It warns that grub has to be written to the appropriate boot devices in order for it to stay in sync.

If you are unsure of which is the designated drive, you could install it to all drives.

Note: It is possible to install grub to partition boot records, and some appropriate partitions are offered here....... but this is not recommended.
*****

My system has:
Service partition dev/sda1
System Reserved (bootable) dev/sda2
Win7 dev/sda3
Extended container dev/sda4
Linux File Sys dev/sda5
Linux Swap dev/sda6

The grub warning install dialogue box offers two click to choose options:

1. dev/sda (the hard drive in its entirety with its model number etc)
2. dev/sda5

Now I'm guessing that grub is installed in system reserved dev/sda2
because it contains a boot dir and a bootmgr file.

So I'm a bit confused.

I guess I can click the 'Forward' button, perhaps without making any choice of the 2 options.
OR
Perhaps I must make a choice, but neither of the choices are dev/sda2

Further, the help file tells me that I have been offered partition options that are not recommended, yet you could hardly call dev/sda a 'partition'.

On top of all this - I don't know why my boot disk unique identifier has changed.

Yes, I did do a re-install, but this did not touch dev/sda2 ntfs sys reserved.
In addition, I have updated a couple of times since the re-install and have not experienced this problem.

So:

1. Does anybody know what has caused this problem?
2. Can anybody confidently advise me on my next action vis a vis the 'Forward' button, or the clickable options?

Thanks!

---

### Post by dino99 on 2012-10-02
Sadly you dont tell about your hardware config: is it a bios or an uefi system ?

i suppose that your /dev/sda2 is a ntfs partition (windows) because usually grub should be installed on /dev/sda

open a terminal:
- for installation : [HTML]sudo grub-install /dev/sda[/HTML]
- or for reconfiguration , if grub is installed : 
 [HTML]sudo dpkg-reconfigure grub-pc[/HTML]

otherwise if its an uefi system:

[HTML]https://help.ubuntu.com/community/UEFIBooting[/HTML]

---

### Post by oldfred on 2012-10-02
As Dino says either the MBR or you have UEFI and then you should have grub-efi not grub-pc.

Do not install to a partition. And whatever you do do not install to any Windows NTFS partitions as Windows has vital info in the NTFS partition boot sector.

Grub remembers where to reinstall and your UUID or device changed somehow. Did you reinstall grub at some point?

If you cannot boot:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Use same version of Ubuntu liveCD and add Boot-Repair after you boot. Or download full repair CD version of Boot-Repair.

---

### Post by Ace..... on 2012-10-02
1. The system is surely bios based rather than UEFI as I have not heard of the latter.
(I can access my bios on restart as per usual method.)

2. dev/sda2 is ntfs

Note:

I installed ubuntu as a dual boot to win 7, following the automated procedure.
Therefore, wherever the automated procedure places the boot manager, then that is where it will be.

I presumed that this is in dev/sda2 simply because I can see a boot dir and a file called bootmgr. 

I don't know how this tallies with your statement that:
"usually grub should be installed on /dev/sda"

The thing is, I don't know what I'm looking for.
Is there a file called grub that I can find?

I am a bit concerned that this problem should have occurred.
The last install, a couple of days ago was 'Transmission' a torrent downloader, which I used for downloading some avi files.
I figured these would be safe, but perhaps I have been stuffed - I have no idea really.

I have not rebooted since then...... and I don't really want to until this problem is sorted.

As I see it, I have 2 options:

1. Establish where' ubuntu install' places the grub file, and find it and verify it, and then find out what to do next.

2. Do something with 'Configuring GRUB-PC'
ie. click 'Forward' or choose an option, or close it down.

At the moment it is just sat there awaiting input, with the update manager stalled in the background.

It may not be wise to start running terminal commands while update is half way thru its process, and 'Configure GRUB-PC' is awaiting action.

what do you think?

(BTW: I have not reinstalled GRUB - I merely re-installed ubuntu using the 'keep home' method, and all has been ok for a month now, and loads of reboots)

---

### Post by oldfred on 2012-10-02
Boot loaders whether grub or Windows are in the MBR which is the very first sector of a hard drive. BIOS finds hardware and jumps to the MBR to continue to boot. Since MBR is tiny most boot loaders now have additional code some where else. Grub has folders in /boot and other locations in Ubuntu.

Bootmgr is the Windows program that is used for booting Windows. It only boots Windows and does not even see any other installs. Windows goes from MBR, to NTFS PBR or partition boot sector to Bootmgr to load Vista or Windows 7. 

If you run the BootInfo report it shows details of what is installed in all MBR, PBR and what boot files are installed. Good just to document system or understand boot process, but a lot of detail.

---

### Post by Ace..... on 2012-10-02
I've been having a think (and just read OldFreds last note 1 min ago)......

Dino99 suggests 2 options:

```
sudo grub-install /dev/sda
```
```
sudo dpkg-reconfigure grub-pc
```

We know that I already have a dual boot, so grub is already installed, AND the help file tells us that the problem relates to a missing drive, OR a drive that has lost its unique identifier.

Clearly the help file may not cover all options, but lets assume its correct.

Something has screwed up the identifier...... first suspect must be the torrents as its the only downloads that might be considered risky (I'll start another thread on that).

I could go for the above reconfigure command, but that still leaves me with an open process running ie the update manager and Configure GRUB-PC.

I note that there is no 'x' to close this process down.
This seems to mean that I need to make a move, and then reboot, keeping fingers crossed (the wings are icing........ but let's go for it).

So I'm looking at OldFreds suggestion of creating a BootInfo report.

This makes a lot of sense, cos it might also indicate what has caused this prob in the first place.

BTW @OldFred I had arrived at the conclusion that Boot & bootmgr must be windows related, but thanks for confirming that.

Back to bootinfo..... I think I will leave update manager running and stalled, and run:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```and then:
```
sudo apt-get install -y boot-repair && boot-repair
```This should launch the boot repair prog, displayng a number of tabs, one of which is 'Other Options'.
I'll click on 'create bootinfo summary' and 'participate to statistics of use'

The latter sounds like it will upload stats to assist further development.

I'll try that now.

---

### Post by Ace..... on 2012-10-02
1st command result:
******
you are about to add the following PPA to your system:
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.KRXRr6ZBrE --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 3C48D16124B50277AF10D27F32B18A1260D8DA0B
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
******

Looks a bit like a fail.

lets try the 2nd command:

******
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
*******

Okay....... another fail.
Damn.
We can't even launch boot repair.
Hmmmm.

---

### Post by Ace..... on 2012-10-02
Thinking again.....

We maybe need to close down 'update manage' and or 'Configure GRUB-PC'

I reckon that is what is locking access to boot repair.

What do you think?

---

### Post by oldfred on 2012-10-02
I think you have a conflict.  Close down the other tasks.

I often open synaptic but then try to run an install command and get similar conflicts. 

Boot info does not show this which is the location that grub expects to reinstall into.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by Ace..... on 2012-10-02
ok.... i now have running:
Firefox
Update manager
Configure GRUB-PC
Terminal
I'm now gonna run:

```
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub 	

```

---

### Post by Ace..... on 2012-10-02
1st command:
```
sudo debconf-show grub-pc
```*******
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-HTS541040G9SA00_MPBBLAX2JVJGMG
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10
*****

2nd command:

```
sudo grub-probe -t device /boot/grub
```
*******
/dev/sda5
*******

That's it!

---

### Post by oldfred on 2012-10-02
The first command says it will install to this drive, Is that still one of your drives:

> grub-pc/install_devices: /dev/disk/by-id/ata-HTS541040G9SA00_MPBBLAX2JVJGMG

The second shows this:
> /dev/sda5

Which is installing to the partition. It needs to be installed to the MBR or sda not sda5 as Dino originally suggested with either or both commands he posted. If they do not work, then you can use Boot-Repair.

---

### Post by YannBuntu on 2012-10-03
> **Ace..... said:**
> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

As mentioned by Oldfred, this looks like another package manager is activated (maybe the Update-Manager, which sometimes automatically appears at startup).

Alternatively, you can use Boot-Repair from [Boot-Repair-Disk or Ubuntu-Secure]("https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair").

---

### Post by Ace..... on 2012-10-03
The last information was good, and the pieces of the puzzle are dropping into place.

The drive listed:
```

grub-pc/install_devices: /dev/disk/by-id/ata-HTS541040G9SA00_MPBBLAX2JVJGMG
```This is my USB drive; originally the hard drive of an earlier laptop.
Meaning that it was bootable (to winXP).

I used this as a storage drive, but had not formatted - I'd kept my old data and winXP as it was - the idea being that I had another OS with all my data.

After the Ubuntu re-install project last month (after loss of desktop) - I had a big clear out of pointless programs and data on this USB HD, leading to repartitioning - the first 50% being formatted to EXT4 (the latter 50% ntfs but that's irrelevant).

From the screen-shot below, you'll see that the drive contains the Master Boot Record (MBR).
The EXT4 Volume partition flag is set to bootable.

**So What Happened - how did GRUB get written to the USB drive?**

Two possibilities (that I see):

********
1. I had the USB drive connected during Ubuntu re-install (using the 'keep home' method).

Perhaps 'Install' auto recognised the MBR present on the USB HD and wrote grub to it.
If this was the case, the actual fixed HD would already have had grub written to it from the initial Ubuntu install - hence why the PC will reboot without the USB HD attached.

2.  I then re-formatted the USB HD primary partition using EXT4 file system.

I have no memory of choosing it to be bootable, but perhaps gparted recognised it as bootable and defaulted to setting it to be bootable.

Presumably the MBR points to the multi-boot manager, no doubt located on dev/sda5 - the fixed HD partition containing the Ubuntu file system.
If this is the case, it wouldn't matter that the USB HD was formatted blank, as long as the USB MBR pointed to the fixed HD.
********

If the above is correct, the Update Manager threw up the problem, simply because I had disconnected the USB HD.

BTW the bios boot sequence is not set to boot from the USB HD first, so this has not been tested.

My thinking is that once this problem has been cleared up, I can place the USB HD first in the boot sequence, and see if the multi-boot screen is displayed.

**What To Do Now?**

I still have Update Manager running but stalled awaiting action vis a vis 'Configure GRUB-PC'

My guess is that this is the GUI for Dino's commands:

```
sudo grub-install /dev/sda
``````
sudo dpkg-reconfigure grub-pc
```Therefore, If I choose the option to install to dev/sda (the fixed HD) - it will re-write the boot instructions to the MBR, and everything will be fine.

Note I will not click the second option to install to dev/sda5.

I think that is logic, but I note that YannBuntu has posted, so I'll stall a bit and see if he agrees with this course of action.

---

### Post by Ace..... on 2012-10-03
So I clicked the 'install to dev/sda'
and then clicked 'Forward'.

The subsequent screen offered a click option to 'continue without installing GRUB'

hmmmm..... I did click dev/sda didn't I?
Surely I did...... I'm not stupid (am I?)

There is no back button.

I check the help file and it is of course full of dire warnings vis a vis not installing GRUB.

below is the screenshot

It ends up by saying 'I should install GRUB somewhere'

Maybe if I click Forward without clicking the option box, it might take me back.

Yes..... it took me back to the previous screen, and yes, I had clicked 'install to dev/sda'

Very confusing this.

I'm gonna continue using the only option available to me, which is to accept not to install GRUB.
*******

Okay..... Configure GRUB-PC has gone, and I'm left with Update manager with 9 updates @ 12.9Mb.

I'll install that lot after checking boot repair

---

### Post by Ace..... on 2012-10-03
Ran boot repair command

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
``````
sudo apt-get install -y boot-repair && boot-repair
```

The following output was seen in terminal, yet strangely it did not end.
There is no typical command prompt.
Terminal is just sat there at the last line : 
```
Setting up pastebinit (1.3-2ubuntu2.1) ...
```
```
sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-nonfree gawk glade2script libsigsegv2 pastebinit
  python-configobj
Suggested packages:
  lvm2 mdadm mbr clean-ubiquity os-uninstaller
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-nonfree gawk glade2script libsigsegv2
  pastebinit python-configobj
0 upgraded, 8 newly installed, 0 to remove and 13 not upgraded.
Need to get 1,311 kB of archives.
After this operation, 5,708 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-sav all 3.193-0ppa39~precise [305 kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ precise/main libsigsegv2 amd64 2.9-4ubuntu2 [14.6 kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ precise/main gawk amd64 1:3.1.8+dfsg-0.1ubuntu1 [465 kB]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ precise/main python-configobj all 4.7.2+ds-3build1 [233 kB]
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main glade2script all 0.3.2.1-0ppa7~precise [40.5 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-repair all 3.193-0ppa22~precise [90.8 kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/universe pastebinit all 1.3-2ubuntu2.1 [16.1 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ precise/main boot-sav-nonfree all 3.18-0ppa20~precise [146 kB]
Fetched 1,311 kB in 2s (462 kB/s)     
Selecting previously unselected package libsigsegv2.
(Reading database ... 207758 files and directories currently installed.)
Unpacking libsigsegv2 (from .../libsigsegv2_2.9-4ubuntu2_amd64.deb) ...
Setting up libsigsegv2 (2.9-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package gawk.
(Reading database ... 207766 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.8+dfsg-0.1ubuntu1_amd64.deb) ...
Selecting previously unselected package boot-sav.
Unpacking boot-sav (from .../boot-sav_3.193-0ppa39~precise_all.deb) ...
Selecting previously unselected package glade2script.
Unpacking glade2script (from .../glade2script_0.3.2.1-0ppa7~precise_all.deb) ...
Selecting previously unselected package boot-repair.
Unpacking boot-repair (from .../boot-repair_3.193-0ppa22~precise_all.deb) ...
Selecting previously unselected package boot-sav-nonfree.
Unpacking boot-sav-nonfree (from .../boot-sav-nonfree_3.18-0ppa20~precise_all.deb) ...
Selecting previously unselected package python-configobj.
Unpacking python-configobj (from .../python-configobj_4.7.2+ds-3build1_all.deb) ...
Selecting previously unselected package pastebinit.
Unpacking pastebinit (from .../pastebinit_1.3-2ubuntu2.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Setting up gawk (1:3.1.8+dfsg-0.1ubuntu1) ...
Setting up boot-sav (3.193-0ppa39~precise) ...
Setting up glade2script (0.3.2.1-0ppa7~precise) ...
Setting up boot-repair (3.193-0ppa22~precise) ...
Setting up boot-sav-nonfree (3.18-0ppa20~precise) ...
Setting up python-configobj (4.7.2+ds-3build1) ...
Setting up pastebinit (1.3-2ubuntu2.1) ...
```

I then ran 'create bootinfo' as was suggested by OldFred

And here it is:

[http://paste.ubuntu.com/1257749/](http://paste.ubuntu.com/1257749/)

I wonder if there is any harm from running boot repair, and letting it repair the boot.

Or perhaps I should quit, and reboot, and see if everything works.
If not, boot from cd, and run boot repair.

---

### Post by YannBuntu on 2012-10-03
> **Ace..... said:**
> And here it is:

[http://paste.ubuntu.com/1257749/](http://paste.ubuntu.com/1257749/)

Here is what i would do:
1) Reboot the PC, and check if you have access to Ubuntu and Windows
2) If not, try the "Recommended repair" (it will reinstall grub-pc in the MBR, no possible harm), indicate the new URL that will appear. Then reboot.
3) If you still can't see the GRUB menu, via Gparted reduce your sda5 partition from 376GB to 375GB, in order to create a 1GB /boot partition at the very start of your extended partition. [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

### Post by Ace..... on 2012-10-03
Just thinking......

Maybe Terminal is waiting for me to install the updates.
It did ask me if I wanted to install them, but I thought it had done that itself.

I'll do it.

Also I note that the pastebin reported:


```
ADDITIONAL INFORMATION : =================== log of boot-repair 2012-10-03__13h13 =================== boot-repair version : 3.193-0ppa22~precise boot-sav version : 3.193-0ppa39~precise glade2script version : 0.3.2.1-0ppa7~precise boot-sav-nonfree version : 3.18-0ppa20~precise W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59  0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
```

1 reinstalled.
Could this be then that Config GRUB-PC did in fact install the boot files again to dev/sda even though it reported that it wasn't going to do so?

---

### Post by Ace..... on 2012-10-03
I installed all updates, and hey presto...
Terminal completed its output:

```
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 70, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 70, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/glade2script", line 2339, in set_widget
    exec( arg )
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Failed to open file 'boot-repair.png': No such file or directory
```

I'm gonna reboot now.

---

### Post by Ace..... on 2012-10-03
Yes!
The assumed logical thinking turned out to be correct.

I first rebooted from the Fixed HD.

I then modded my bios boot sequence and placed the USB HD at the top.
Followed by the ubuntu CD - this to allow me to see that the USB HD had failed, if it was going to fail.

But no...... the pc booted to the multi-boot screen from the USB HD.

So that was the problem.
By disconnecting the USB HD before update, this confused Configure GRUB-PC.

What do I do now?
Maybe nothing - everything is running okay.

Does this mean that if I run update again without the USB HD attached, I'll have the same warning come up?

While it's good to know that I now have 2 extra boot methods:

1. Ubuntu CD
2. USB HD

I'd rather have my fixed HD being the focus of any future grub updates (rather than the USB HD).

Does this mean that I should run boot repair with my USB HD disconnected?

Anyway, at least I've learned a lot AND the sys is working fine.
Reason to be cheerful :P

Just gotta figure out how to add ```
--disable-bundled-ppapi-flash %U
```
to the google chrome launch icon, and then I'm about sorted.

---

### Post by Ace..... on 2012-10-03
> **YannBuntu said:**
> Here is what i would do:
1) Reboot the PC, and check if you have access to Ubuntu and Windows
2) If not, try the "Recommended repair" (it will reinstall grub-pc in the MBR, no possible harm), indicate the new URL that will appear. Then reboot.
3) If you still can't see the GRUB menu, via Gparted reduce your sda5 partition from 376GB to 375GB, in order to create a 1GB /boot partition at the very start of your extended partition. [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

Thanks YannBuntu.
I missed this as it was posted just before my post.

As it happens you suggested what I'd made up my mind to do.

But what about that Configure GRUB-PC warning that it was not going to install GRUB, even though I had clicked to install to dev/sda?

It was confusing.

And in Additional Info, where it said 1 re-installed...... was that GRUB re-installed to dev/sda?

---

### Post by YannBuntu on 2012-10-03
From your installed Ubuntu session, please type and indicate the output of:
```
sudo debconf-show grub-pc | grep s:
```

---

### Post by Ace..... on 2012-10-03
> **YannBuntu said:**
> From your installed Ubuntu session, please type and indicate the output of:
```
sudo debconf-show grub-pc | grep s:
```


I am currently booted from the USB HD.

The output from above command is:

```
* grub-pc/install_devices:
```

The last 's:' is coloured red.

I'll reboot from the fixed HD and run it again.

---

### Post by Ace..... on 2012-10-03
I just rebooted from the fixed HD and the response is exactly the same:

```
* grub-pc/install_devices:
```

---

### Post by YannBuntu on 2012-10-03
> **Ace..... said:**
> I just rebooted from the fixed HD and the response is exactly the same:

```
* grub-pc/install_devices:
```

ok, so it should be ok now.

Now, please connect your USB disk, then run Boot-Repair --> Create a BootInfo summary, and tell us the new URL.

---

### Post by Ace..... on 2012-10-03
Okay.
I'm not booting from USB HD..... I'm simply connecting it.

It has been recognised, so here goes with boot repair

Or 

Do you mean just create a bootinfo report (to produce the url)?

I have not as yet run the actual boot repair.

---

### Post by Ace..... on 2012-10-03
here is the url:

[http://paste.ubuntu.com/1258004/](http://paste.ubuntu.com/1258004/)

---

### Post by Ace..... on 2012-10-03
BTW I think this bootinfo report is fantastic and in my opinion, everybody should run it.

You then get a comprehensive report available to you from any computer, if your own has crashed.

I note that it confirms the warning shown on disk utility, that my extended partition is misaligned - it doesn't start on a cylinder boundary.

disk utility warns that performance will suffer.

I had googled this and opinion seemed to be that because this was the extended partition container, it made no difference.

I wonder?

I do have 52Gb of free space to the left of this partition (that I can do nothing with cos windows uses 3 primary partitions: service, reserved, win7.

Perhaps I should move the partition to the left, and attempt to rectify this fault.

I also note that at the end of the report, it makes recommendations for repair, additionally warning that my boot files are far from the start of the disk.....
... presumably because they are located after all the windows partitions.

It seems to work okay though.

Anyway..... it is clearly a useful utility. ;)

---

### Post by YannBuntu on 2012-10-03
The first stage of GRUB is installed in the MBRs of your 2 disks.
So:
- when your USB disk is disconnected, your PC boots directly from the MBR of your hard disk. --> this works.
- when your USB disk is connected, your PC will try to boot from the MBR of your USB disk. --> this may work or not, please try and tell me.

---

### Post by Ace..... on 2012-10-03
> **YannBuntu said:**
> 
- when your USB disk is connected, your PC will try to boot from the MBR of your USB disk. --> this may work or not, please try and tell me.

I have completed this test.

I modified the bios boot sequence, placing:

1.  USB HD 
2. Ubuntu CD
3. Fixed HD

I did this so that if USB HD boot failed I would physically see and hear the PC booting into ubuntu from the CD.

This did not happen so it must have booted from the USB HD.

I have still not run boot repair, other than Configure GRUB-PC, where I chose to install to dev/sda, and where Configure GRUB-PC then told me it was not going to install GRUB anywhere.

I can confirm that the PC will boot from all the 3 sources above.

---

### Post by JKyleOKC on 2012-10-03
Just a FYI note for Fred and Yann. The initial post says:
> **Ace..... said:**
> My system has:
Service partition dev/sda1
System Reserved (bootable) dev/sda2
Win7 dev/sda3
[COLOR=Red]Extended container[/COLOR] dev/sda4
Linux File Sys dev/sda5
Linux Swap dev/sda6That's a pretty solid indication that Ace's system is MBR Legacy, not UEFI!

And I agree with Ace that the report from Boot-Repair is far better than the one usually recommended, especially since it makes the report available from other machines!

---

### Post by Ace..... on 2012-10-03
So what is the current thinking?

The final section of bootinfo report states:

**********
=================== Final advice in case of recommended repair 
Please do not forget to make your BIOS boot on sda (500GB) disk!  
The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. 
Your BIOS may not detect them. 
You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). 
This can be performed via tools such as gParted. 
Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. 
([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))  

=================== Default settings Recommended-Repair 
This setting would reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS). 
Additional repair would be performed: 
unhide-bootmenu-10s   
fix-windows-boot
***********

I note the report states:
"Final advice in case of recommended repair"

Does that mean 'it is recommending repair', or in case I need to repair..

I also note that an additional repair would be performed re:
"unhide-bootmenu-10s   fix-windows-boot"

So, should I run repair?

---

### Post by JKyleOKC on 2012-10-03
My rule is "When it works, don't fix it." If things are working properly for you, just leave it as-is. Those warnings and suggestions are generic, and don't necessarily indicate problems in every case.

---

### Post by YannBuntu on 2012-10-03
> **JKyleOKC said:**
> My rule is "When it works, don't fix it." If things are working properly for you, just leave it as-is. Those warnings and suggestions are generic, and don't necessarily indicate problems in every case.

+1

Happy Ubuntu-ing :)

---

### Post by Ace..... on 2012-10-04
That's great.
Thanks to everybody who has contributed.

This is another problem that we can mark as solved.

:p:p:p:P

---

