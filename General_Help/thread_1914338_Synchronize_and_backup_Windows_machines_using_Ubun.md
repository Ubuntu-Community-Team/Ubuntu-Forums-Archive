---
title: "Synchronize and backup Windows machines using Ubuntu"
date: 2012-01-24
forum: General Help
---

### Post by Cyclonit on 2012-01-24
Hi,

this is actually the very first project using Linux for me so please be gentle and patient with me ^^'

The general idea of this project is using a NAS to synchronize and backup my laptop and my PC. Both my PC and my laptop are running Windows 7 64bits while I plan to install Ubuntu on my NAS. Because I often reinstall my Windows machines I'd like to have as much of the actual work to be done by the NAS itself.
Currently I think the best way of keeping my machines synced and protecting my files from myself would be the following:

- Synchronize the NAS with both Laptop and PC
- Backup the NAS' directory used for synchronizing using incremental snapshots

I thought of several scripts I'd need:

sync_laptop
sync_pc
snapshot_15m
snapshot_4h
snapshot_1d
snapshot_1w

Writing all of those scripts is no problem (I'd use rsync in all of them), the difficulty for me is getting them running when I need them. All of the snapshots could be scheduled using cron easily. That's no big deal at all (especially because all of the copying is between the NAS sync-drive and it's backup-drive). But how can I trigger the synchronization when I need it? There are four situations when they should run:

1. NAS wakes up
2. PC goes online
3. Laptop goes online
4. Either laptop or pc modify/create/delete a file.

The first one is pretty easy I guess. But situations 2 to 4 are a little bit more complicated I guess. I'd have to have some kind of network watcher for 2 and 3 and a platform independent file monitoring. Does something like that exist? Another problem would be ensuring the synchronizing scripts would not show errors all the time if one of the mounted windows drives is not accessible.

A final "dream" would be a .bat script used on my windows machines triggering a synchronization but everything else is more important to me ^^.

Thank you in advance =)

Cyclonit

---

