---
title: "help with failing disks in raid set"
date: 2009-07-02
forum: General Help
---

### Post by meecect on 2009-07-02
Hi, 

This question is not specific to ubuntu, but I'm asking it here because these forums get much more traffic and I'm sure I'll be able to translate the advice to my specific problem.

I have a WD MyBook World edition NAS.  Inside it has a 2 500GB drives, which were put together via software RAID ( md tools ) for 1TB of storage.  I had modified the software that shipped on the device and installed optware, so I had a pretty full functioning server.

Recently I started to get some corruption and noticed loads of FS errors in /var/log/messages.   The errors indicated a hard drive failing, so I shut the system down.

Now I have yanked the drives out and would like to attach them to a known good system to see if I can fix them there.  I just don't trust the little NAS system to give me any good reliable diagnosis.

Is it possible to do this troubleshooting through an external USB enclosure?  In other words can I either:

1) look at each drive individually, or
2) use two enclosures and mount my md volume from USB

If I get them mounted, or at least recognized, what are my next troubleshooting steps?  Is it possible to save just half of the drive?

If I only plug in one drive at a time is there any thing I can do to it that won't screw up the MD volume it had on it?  Can I fsck it safely?  Can I mount it and get any data?

I don't have access to a linux system that I can plug these drives into internally ( or at least not a system convenient for me to do this) so I am hoping that USB will be an option.

The goal is to just get as much (or any ) data off that I can and then determine if one or both are bad and then recycle the good one(s) to another purpose, as I don't really need the NAS anymore.


An additional wrinkle is that I'd like to do my troubleshooting with a Hardy VM running in VMware fusion from my macbook pro.

Thanks,
Cliff

---

### Post by ronparent on 2009-07-03
If it is a raid0 it is a 'stripped' drive which means that sectors are written alternately to both drives. There is little likelyhood of recovering any data from them separately. Lkewise if it a spanning raid, the partition table is on the first drive and the drives cannot be accessed separately. If the raid was originally setup via a mb riad chip, you won't have access to the drives except through an identical mb chipset. 

Your best bet may be to plug back into the original ports, in the same order, and get them to wok long enough to backup essential info.

---

