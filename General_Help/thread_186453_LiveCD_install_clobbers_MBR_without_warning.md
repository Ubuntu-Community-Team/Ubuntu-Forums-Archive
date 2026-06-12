---
title: "LiveCD install clobbers MBR without warning?"
date: 2006-06-02
forum: General Help
---

### Post by elamericano on 2006-06-02
I installed from the LiveCD, and I thought I missed the option to install grub to /dev/hda2, as I always do. However, the resulting erasure of my MBR was so unfriendly that I had to go back and check. I don't see any way to write the bootloader to the partition. I definitely don't agree with not allowing the option. Sure, make mbr the default if you think that's the majority, but it's no more confusing than selecting mountpoints. It *is* a manual partition, after all, and there is no technical difficulty to include it in a graphical installer either.

My last point, and this is beyond question, I think: When I am warned in the last step that /dev/hda1 and /dev/hda5 are going to be formatted, I should be told that the MBR is about to be overwritten. This is destructive write with no backup saved anywhere, right? That's simply common courtesy.

If the option exists, then I'm wrong, but I couldn't find it.

P.S. I know there's the alternate installer, but this should be in the manual section of the most basic installer that exists.

---

### Post by rcarring on 2006-06-02
I can confirm that the text mode install cd did ask me where I wanted grub to live.

---

### Post by apollyonis on 2006-06-02
It appears that they wanted to reduce the confusion and "hassles" in the graphical install from the Live!CD for the beginner or average user. I'm glad that there's still a text mode install that has all of the options. I'm sure this wasn't totally intentional, but rather to try to make it easier for those making a transition into Linux and a new Operating System.

---

### Post by elamericano on 2006-06-02
Reduce confusion? The manual partitioning spans two dialogs and exposes the partition table, the file system types, primary and logical drives (if I recall). The user has to know which partitions to reformat and where to create / and /swap, and they have the option to create more mount points if they want. An "MBR (Default)" selection with a change button would be appropriate and consistent with the usability of this path. It seems illogical to take this one universal function out and think you've accomplished something.

Ok, so I disagree. Someone must have thought it would be less maintenance if they forced users to do it that way. Or it was just a mistake.

But I do think it's a bug not to include it in the list of changes on the confirmation page. I didn't select it, so it's a silent, destructive change. People could have System Commander, Boot Magic, or even just the Windows MBR that they might no longer have the original media to replace.

Who's with me on this? :-)

---

### Post by Athropos on 2006-06-02
[QUOTE=elamericano]Who's with me on this? :-)[/QUOTE]

I agree...

Yesterday, I tried to install a clean Dapper on my laptop from the desktop CD. The partition manager :
 - forced me to give mount points to partitions I don't want to mount (dell recovery, windows...)
 - crashed when it tried to format a newly created partition : I believe that numbers changed (I deleted hda6 to create two new partitions, and hda7 was automatically 'shifted' to hda6) and the partition manager was confused because of this.
 - didn't ask me which filesystem to use to format the existing new partition after I relaunched it. It chose to use ext3, I wanted reiserfs...
 - is confusing when the 'pending changes' panel appears.

I'm now downloading the alternate install cd :)

---

### Post by todak on 2006-06-02
Remember that Ubuntu is meant for the vast majority of people who have no idea what a partition or bootloader is. They will have one hard drive and an Ubuntu disk with which to install to that single drive. They do not want a bunch of questions asked of them about things of which they do not know. It must be simple and reliable for them to install within a graphical environment, with the least amount of input from the user, to get things taken care of by the installation routine on the disk. For that reason, the desktop CD will automatically place the bootloader on the MBR without any input from the person performing the installation. A lot of GNU/Linux experimenters (myself included) dual, triple and sometimes quad boot various operating systems as a matter of course, without thinking about whether to load grub, lilo, etc. and onto which partition of a particular disk it should be placed or which entry in menu.lst should be the default OS at boot time. That is routine for me. However, the newcomer wants the installation to be as easy and friendly as possible.

---

### Post by aysiu on 2006-06-02
I think it's fine that they "clobber" the MBR without warning so long as they still continue to offer the text-mode installer on the "alternate" CD.

I did get annoyed that I was forced to mount every partition--that just seems stupid, since it doesn't simplify anything at all. Not asking users about Grub does simplify things a bit, even if it does do smeothing without the user's consent.

---

### Post by Athropos on 2006-06-02
[QUOTE=aysiu]I think it's fine that they "clobber" the MBR without warning so long as they still continue to offer the text-mode installer on the "alternate" CD.
[/QUOTE]

They should change the description of the alternate CD: I myself downloaded and tried the desktop CD because I believed it was the same as the old install CD.

```

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 192MB of RAM. 

```

I don't think that my case fit in these situations, I just want to install Ubuntu with a few more options than the desktop cd has.

---

### Post by joshrobinson on 2006-06-02
i just like the live/desktop cd because its faster :-D i run ubuntu and only ubuntu.. so clobber away at my MBR 

at least it adds windows in the list so people can still get to that

---

### Post by rcarring on 2006-06-02
I specifically wanted the alternate mode cd for the very reason that it

a) had a basic build on it complete with packages and once installed will act as a repository

b) allows me to install gcc which I need to recompile my vmware modules under the new kernel

c) loads pretty fast with good old blue and white text screens with red buttons

d) allows me to tell grub where it can live -- which is obviously not the case with the Live CD

(I have done Live CD installs too, only to find that there were NO kernel headers available online for the 22 build kernel that was beta 2 live.)

---

### Post by elamericano on 2006-06-02
[QUOTE=todak]Remember that Ubuntu is meant for the vast majority of people who have no idea what a partition or bootloader is...[/QUOTE]
Oh no, we need to guard against these "here's why it doesn't matter" explanations. Firstly, the newbies won't be doing custom partitioning ("They don't know what a partition is"). Secondly, ease-of-use and functionality are not mutually exclusive. The people who need it could use it, those who don't understand would see it is the default choice and leave it alone.

I'm all for the battle against feature-creep, but you can't use that to justify anything. Makes you wonder why there's manual partitioning at all. Ubuntu should just do what it thinks is best for the user, right? We wouldn't want to confuse anyone, after all.

No wait, there was something about just having to work, right? Darn these technicalities. Maybe nuking people's pre-existing bootloaders isn't the right thing to do after all. :-k

---

### Post by ericesque on 2006-06-02
wow.  this one is kinda a tough call, but I think I agree with elamericano.  If you're going to give me the option to manually edit the partition table, you have to let me decide where to install grub.  Either allow more advanced users to be advanced, or I say employ KISS to no end and remove the option to manually edit the partition table.  
At the barest of minimums, at least warn the poor sap before you zap his MBR!

---

### Post by mrbanana on 2006-06-02
Quite a few system backup programmes use the mbr, trueimage is one, and so is bootitng.  Both are hard drive backup/partitioning programmes.

If a trueimage user backs up their partitions to a protected/hidden partition on their hdd and the live cd overwrites the mbr, they won't be able to restore their backups without a trueimage boot cd or simply reinstalling trueimage and wiping grub's mbr settings, so no Ubuntu access.

Anyone with a Dell laptop will also have a hell of time restoring the mbr so they can access their restore partition, which uses a cut down version of Powerquest's Driveimage.  I know, I did it once and the hoops you have to jump through to get the partition table and mbr setup back to factory default so you can use their stupid restore function is a real pain.

Automatically installing to the mbr with no option to change it is a very bad idea.

---

### Post by sunset on 2006-06-02
I agree that the Desktop CD should offer an option for where to install grub.  I was also annoyed that it doesn't offer reiserfs as a formatting option.

For these reasons it also seems wrong to blanketly say that the desktop CD is the "recommended" way to install, without further elaboration.  IMO the Alternative CD is a better general-purpose choice, especially for non-newbies.

By the way for those who complained that the Desktop CD forces you to mount all partitions, this is not true.  You can get around that by select the empty (first) listbox entry for the partition name in addition to that for the mount point.  Not optimal, but it works.

---

### Post by aysiu on 2006-06-02
I think what would make sense is asking about Grub *if* someone selects "Manually edit the partition table."

If someone selects "Erase entire hard drive" or "automatically resize and use free space," the installer shouldn't ask where to install Grub.

---

### Post by nixt on 2006-06-02
One thing i'm not too positive about the installer, is the partitioner.

Remember the part where they ask you whether you wish to use all free space, LVM or manually edit the partition table? I went a bit too fast with the keyboard and chose the wrong option (LVM). 

My partition table got wrecked immediately, with all partitions gone! I had to use an Acronis tool to get one very essential partition back. Wasted a few hours.

I wonder if there should be some "Yes/No do you REALLY WANT TO DO THIS" confirmation dialog before potentially destructive actions take place.

---

### Post by aysiu on 2006-06-02
[QUOTE=nixt]
I wonder if there should be some "Yes/No do you REALLY WANT TO DO THIS" confirmation dialog before potentially destructive actions take place.[/QUOTE] Isn't there one already?

---

### Post by nixt on 2006-06-02
Sorry if I caused some confusion.. i was referring to the text-based one when you boot off the alternate CD.

---

