---
title: "File system for Mac compatability"
date: 2011-05-23
forum: General Help
---

### Post by aaronsharpe on 2011-05-23
I have some data on a server that both me and a colleague need offline access to. Unfortunately I use Ubuntu (11.04) and my colleague uses a Mac. 

I have a 2TB drive and the data has file sizes up to 300GB, but mostly in the 10s of GB.

The research I have done suggests we might have a problem with HFS as the data might get corrupted, is this a problem in 11.04? Or can someone suggest the best file system to use.

Normally I would just try my chances and hope it works, but loss of access to the data for any length of time puts a stop to our work.

Thank you for your help.
Aaron

---

### Post by aphatak on 2011-05-23
Does the server that holds the files run an ssh server?  If it does, both of you could connect to the server with ssh clients, and the file-system on the server wouldn't matter.

If your Ubuntu machine holds the data, you could install the openssh-server on it, and allow the Mac to connect to it.

---

### Post by aaronsharpe on 2011-05-23
Yes aphatak, we usually access the data via SSH and run code that uses the data on the server. However we need offline access, and ssh from one computer to another would be far from ideal, we need to be able to just connect the drive via a USB cable.

We don't both strictly need write access on both computers, only read.

Thanks

---

### Post by eltonw on 2011-05-23
If this is of any help to you:
I have an Asus netbook running ubuntu (ext4), and a Macbook running OSX (HFS). I regularly copy files back and forth between both machines using a USB key. Also, I update my bookmarks using Xmarks (hence this is "offline"). On the Mac I have Safari, Chrome and Firefox browsers. The latter is the browser in use on the netbook.

The only incompatibility I have found VERY RECENTLY: I had burnt a test DVD for "PC + MAC", "Joliet", then HFS+. In all three cases the filenames were truncated, until I burnt the DVD using UDF. 
REF:[http://ubuntuforums.org/showthread.php?t=1758264]("http://ubuntuforums.org/showthread.php?t=1758264")

I have been using ubuntu linux on the netbook for several years, and a mac (HFS) for a similar length of time. To date, I have had no 'data corruption' issues WRT exchanging data between these machines.

... admittedly, I am not sharing files via a network (except for my bookmarks), but perhaps  my comments might  ease some of your concerns. Also, since OSX and linux share a common 'genealogy' viz, *nix... I would venture that interoperability between these OSes should pose little difficulty.

... respectfully,

---

### Post by sanderd17 on 2011-05-23
If you have enough with read on the mac, maybe you can look at ZFS?

---

### Post by aaronsharpe on 2011-05-23
> **sanderd17 said:**
> If you have enough with read on the mac, maybe you can look at ZFS?
Thanks sanderd17, just looked up ZFS and it might work, I don't know how easy the mac drivers will be to install but it looks promising. It's not one I have heard of before.

eltonw, from what I understand there can be problems with large drives and lots of the old stable filesystems that are find on USB keys don't support large file sizes.

Thanks

---

### Post by Joe of loath on 2011-05-23
The number of filesystems that macs support out of the box can be counted on one hand. If you are able to install drivers for ZFS or EXT2/3/4, those will be your best bet. If not, Linux has partial support for HFS+. rw works fine, but only if the FS is unjournaled.

---

### Post by aaronsharpe on 2011-05-23
Looked a little more into ZFS, and it looks like it could be an issue for both me on linux, my colleague on mac and our linux server. As it isn't natively supported.

I think the solution might be to buy another drive.

---

### Post by Joe of loath on 2011-05-23
Check out macfuse, I believe is has support for native Linux filesystems.

---

### Post by srs5694 on 2011-05-23
Why do you want to physically connect the drive to multiple computers with a USB cable? With a fast enough network connection (gigabit Ethernet or even 10-gigabit Ethernet), you're likely to get faster access by using an internal drive on the server and using a network filesystem such as NFS or SMB/CIFS. This will also have the advantage of not jostling the drive around, which could end up damaging your drive and therefore losing your critical data. Finally, using this approach will make it much easier to select a filesystem; just use something that's appropriate for the server OS -- I'd recommend XFS or ext4fs for a filesystem holding files between 10 GB and 300 GB in size.

Alternatively, but in a similar way, you could get yourself an NAS unit and use it rather than a Linux server to host the data drive.

---

### Post by aaronsharpe on 2011-05-23
Ideally we wouldn't use the data on the drive at all. But we need a copy on hand for when we are travelling and don't have a stable Internet connection and also the server we normally use is likely to have some downtime over summer and we need a copy for then. It would also help for when the server is busy.

It looks like it will be easiest to just get a second drive when we need one. For the cost of a drive it's not worth me spending hours trying to set up a workaround.

Thank you everybody for your help.

---

