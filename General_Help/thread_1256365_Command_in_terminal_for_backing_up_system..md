---
title: "Command in terminal for backing up system."
date: 2009-09-02
forum: General Help
---

### Post by hockey97 on 2009-09-02
Hi, I need to make backups from my ubuntu system. 

Currently I messed up the permission settings of the root system.

So I would like to know what are the commands to use in terminal that I can directly backup all files of my hard drive to an external hard drive?

I currently tried using the live cd and I can backup most files and folders but their is still a good chunk missing due to me not using a user that has full rights. 

I even used sudo gksu nautilus and I still get those permission errors. 

I think the mounted external hard drive always mounts as read only. 

I even tried my windows xp since I do have a dual boot of ubuntu and windows xp. 

on xp it gives me writing errors and shows the external hard drive is always read only permission. 

the external hard drive is in ntfs format because I will need it soon for college assignments and it has to work on windows XP without any problems.

---

### Post by hal10000 on 2009-09-02
If you external harddrive has a ntfs filesystem, then it's by default only mounted readonly. You need the ntfs-3g package to ount ntfs devices read-write.

But i would strongly recomment to use an ext3 partition for your backup, because even if you have the ntfs-3g package you would run into problems.

---

### Post by hockey97 on 2009-09-04
ya, but the reason is that I can't use linux particians because I need the external hard drive to be used with my colleges computers which they have only windows xp and won't allow me to install anything on their computers. 

So linux particians can't be read by windows unless you install a driver for windows. 

So I will stick with ntfs for now because I would need to take my external hard drive to load up presentations for my college classes.

I do have ntfs file system package to be able to read ntfs file systems.

What are the commands to backup everything to external hard drive? should I just use the live cd?

---

### Post by fluffman86 on 2009-09-04
@hal10000: ntfs-3g has been in Ubuntu since Gutsy or Feisty.  That's not the issue.

@hockey97: Yeah, just use the live cd to back up your important stuff.  everything should work fine from there.

---

### Post by StuartN on 2009-09-04
I do backups to an external ext3 drive and sometimes do backups from Linux partitions to NTFS and from a Windows Vista NTFS drive to an ext3 partition. Everything works fine under Ubuntu 8.04 and 8.10, although I did install SMBFS because I prefer to manually mount the partitions.

If the drive is read-only then it is probably because you set it (or a directory on it) to read only, or because it was unplugged without stopping it on Windows - all drives have to be safely ejected, and become locked until the next time they are safely ejected.

A good command for backing up to another drive is rsync (man rsync), or Meld (get it through Synaptic) if you want a graphical interface. The two-pane programs like Gnome Commander are good too (my favourite is the synchronise tool in Krusader) and they will give feedback about why and where a backup is failing.

One thing to be wary of is links, especially recursive links, and the attached filesystems under ~/.gvfs and /media. If you try to back up your hard disk by backing up root then you are actually backing up the universe known to your Linux, including the virtual filesystem, devices, mounted filesystems and multiply duplicated directories accessed through links. It is better to either back up specific directories under ~/home or to specifically exclude troublesome directories like ~/.gvfs, /mnt, /media etc.

---

