---
title: "Linux equivalent of System Restore"
date: 2010-02-23
forum: General Help
---

### Post by datpapi on 2010-02-23
Just switching over from WoW(World of Windows) and was wondering if Linux has a feature similiar to the Windows System Restore feature. Being new, I'm afraid I'll muck my system up at some point and would like to have the ability to quickly undo fatal mistakes and restore to a good configuration. 
 
Reading up, I see there are plenty of ways to manually undo changes made using the terminal, but one thing I did like about Windows was having restore points to revert to if needed.
 
Has linux such a feature?

---

### Post by switch10 on 2010-02-23
I make a backup of my /home folder every few days. You can use a GUI program like back in time. It works better than Windows system restore.

---

### Post by datpapi on 2010-02-24
Thanks Switch. I'll check it out.

---

### Post by pastalavista on 2010-02-24
If you have a live CD, you have a restore disk. Just reinstall in MANUAL mode and at the partition editor, UNCHECK all the "format" boxes for every mountpoint. This will install a fresh system without erasing any user files. You'll just have to re-do all the updates again. (be sure to use the exact same user and computer names)

---

### Post by SecretCode on 2010-02-24
Using a live CD as a restore disc is **not** the same thing as window system restore. It's not about rolling back to a freshly-installed system but about rolling back to a **recent** working config.

Backing up /home as suggested is probably the best way to achieve this.

---

### Post by pastalavista on 2010-02-24
> **SecretCode said:**
> Using a live CD as a restore disc is **not** the same thing as window system restore. It's not about rolling back to a freshly-installed system but about rolling back to a **recent** working config.

Backing up /home as suggested is probably the best way to achieve this.

I agree, completely. But if you don't have system restore and haven't backed up anything... totally borked your system.. what cha gonna do?

edit: With the method I described, the /home directory won't change at all but the rest of the / will so also be sure to copy /etc/apt/sources.list from the old installation before you start the reinstall.

edit2: Also, the 'File' menu of Synaptic Package Manager has the option to "generate package download list" which can be saved and imported into the fresh Synaptic to replicate your former installation.

---

### Post by WardXmodem on 2010-02-24
> Backing up /home
but if you've messed up your mount table, your network configuration, etc etc. 

Perhaps someone knows a list of appropriate files that might be changed, that they might be saved very similar to a windows system restore which seems to revert to replaced DLLsl and other things. 

I'm not asking for THAT (e.g. recover from a failed update).. 

but at least, recover -- yes -- /home, but also critical system files. 

What I personally do is write a little alias 
alias dt='date +%y%m%d%H%M'
and a little "backup a file" macro:
function ba ()
{
         cp $1 $1.$(dt)
}

so you could say, for example, ba resolve.conf    before poking about assigning network cards by editing,
and you'd have a resolve.conf.1002241319

---

### Post by SecretCode on 2010-02-24
I consciously but quietly overlooked that ... yes, if you're going to mess about with system settings there are more things to back up. Most of those settings are in the /etc directory. You should probably back up the whole thing, rather than concentrate on specific files. /etc is just 20M on my system.

---

### Post by thrasher6900 on 2010-10-06
> **pastalavista said:**
> If you have a live CD, you have a restore disk. Just reinstall in MANUAL mode and at the partition editor, UNCHECK all the "format" boxes for every mountpoint. This will install a fresh system without erasing any user files. You'll just have to re-do all the updates again. (be sure to use the exact same user and computer names)

O.K so will this work if I have a windows partion, and, if I just upgraded the distro and things like my keyboard won't work?  I noticed a lot of "obsolete files" were deleted on the terminal whilst watching the install.

---

### Post by pastalavista on 2010-10-06
> **thrasher6900 said:**
> O.K so will this work if I have a windows partion, and, if I just upgraded the distro and things like my keyboard won't work?  I noticed a lot of "obsolete files" were deleted on the terminal whilst watching the install.If the live CD works OK, the installation will too. I need to add that you should make a backup copy of /etc/apt/sources.list and replace it after re-installing, before updating.

---

