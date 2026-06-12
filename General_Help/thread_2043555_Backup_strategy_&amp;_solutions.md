---
title: "Backup strategy &amp; solutions"
date: 2012-08-16
forum: General Help
---

### Post by freakalad on 2012-08-16
Hi all,

I've been thinking recently that I need to develop & deploy a more comprehensive backup strategy than the ad-hoc "solution" I use at present. Been putting feelers out for opinions on IRC recently, but thought I should do this is a more structured (& shared) manner

*Some of my current setup:*
* FreeNAS with RAIDZ2 (soon RAIDZ3) - RAID 6
* Ubuntu (currently 12.04.x) server running KVM on LVM2 partitions
* A mix of clients, including various POSIX desktops (Ubuntu, Centos/Fedora, Mac, Android, etc), and a few windows instances for testing
* Gigabit ethernet

*I have a few developments in the works, and a *lot* of "dogfooding":*
* In the process of building a redundant FreeNAS with RAIDZ3 for testing
* Moving my VM data onto my NAS & connecting via iSCSI
* Popping some SQL VM's for replication
* PXE to simplify triage & cloning
* Start to scale down the use of heavy clients & start making use of devices like Hackberry/Raspberry Pi to act as thin-clients for VDi or terminal services (remote-X, VNC, RDP, NX, SPICE, etc), so that I can nuke any client & be up & running to my previous state over PXE - within a margin of 1 day

*What I want to implement at the end of the day:*
* Incremental client backups of hosts/data to the server
* SQL replication to a dedicated (sandboxed) VM
* Host pauses & makes weekly snapshots of VM's
* Redundant NAS does a daily rsync of data on primary NAS
* NAS makes weekly/monthly archives of backed up data & pushes it to the secondary NAS, to removable HDD's/media and/or to an off-site facility, such as TarSnap (Amazon, pier, colo, whatever)
* Periodically test & nuke any archives older than a month

Now I know that rsync (+tar) is the de-facto standard for POSIX, and short of me getting jiggy with with some bash scripting & cron (& probably end up making some really catastrophic typo's), I'm looking for some established systems (& methodologies) I can use for the purpose.
*There are a few good references available on the subject:*
* [http://wiki.linuxquestions.org/wiki/Backup](http://wiki.linuxquestions.org/wiki/Backup)
* [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
Both are good resources, but do not delve into much detail on the systems listed.

*There are a few criteria that I'm trying to keep in mind:* (please keep in mind that this is not only for myself, but stem from interactions & observations with non-techs)
* FLOSS (& active) - I try to encourage people to make use of Open Source Software whenever possible, irrespective of their current OS.
* I've been asked for FLOSS backup solutions on a number of occasions, not all by Linux users, so the system, or at least an agent, needs to have supporte for multiple OS's (.deb, .rpm, win, mac, etc)
** GUI or WebGUI is a big selling-point (probably don't need it myself, but sweetens the deal for newcomers)
* Network support - a client-side agent is OK; not needing one is even better.
* The actual backups/archive need to make sense. I know that a few systems archives (& encrypts) data into monolithic volumes, but if a laymen user was to dig into the data to try & locate a file, it could be off-putting.
* Support for (encrypted) on-line/off-site backup, as well as removable disks (i.e. if they plug a 1TB USB HDD every Friday/weekend)

*I've been looking into, but have not come to any conclusion, wrt a few systems: (just sharing my list)*
* rsync & tar
**  [Grsync]("http://www.opbyte.it/grsync/")
** DeltaCopy
** Synametrics
** cwRsync
** grsync
** [rsnapshot](http://rsnapshot.org)
* [Déjà Dup](http://live.gnome.org/DejaDup)
* Simple Backup & Restore
* [Amanda](http://www.amanda.org/) & [Zmanda](http://www.zmanda.com/)
* [Bacula](http://www.bacula.org/)
* [Duplicity](http://duplicity.nongnu.org/)  & [Duplicati](http://code.google.com/p/duplicati/)
* [BackupPC](http://backuppc.sourceforge.net/)
* Synkron
* [TimeVault](https://wiki.ubuntu.com/TimeVault)
* [FlyBack](http://flyback-project.org/)
* [Back-in-Time](http://backintime.le-web.org/)
* [rdiff-backup](http://www.nongnu.org/rdiff-backup/)
* [Simple Backup](http://sourceforge.net/projects/sbackup/)


*What I'd like to know:*
* Which of these systems have community/forum members been using & what has your observations been?
* Do you know of systems that meet the aforementioned criteria (including any on the list provided)?
* Are there any excellent systems, that meet the criteria, that I do not have on the list?
* Any wisdom you'd like to share?

Any help & insights would be greatly appreciated.

- J

---

