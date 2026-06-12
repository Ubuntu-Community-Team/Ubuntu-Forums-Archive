---
title: "Mount fails because of unexpected inconsistency"
date: 2010-10-15
forum: General Help
---

### Post by GeoMX on 2010-10-15
We are testing Ubuntu as the base for our products, we create custom Karmic installations (debootstrap + some extra packages) and then deploy our software, these systems can start in two different modes: "normal" and "read-only". We must say the system works quite well, but after some time, several systems are showing a common error: they don't start or fail showing an unexpected inconsistency for one of the partitions (every system has one hard disk with four partitions), the message refers to an unexpected inconsistency. When this error appears, a recovery console is started and I can run fsck and answer "yes" to its recommendations, after this the system runs again without errors.
The problem is that this error can appear again at a random time and we need to avoid this "manual fixing" process, I've searched the web and found some references to a bug? in an early Karmic version: [http://ubuntuforums.org/showthread.php?t=1281937](http://ubuntuforums.org/showthread.php?t=1281937)

Besides ALSA 1.0.23, we use only standard Karmic tools (all from the official repositories), we are running the latest kernel update available for Karmic, and don't know whether this inconsistency is caused by our software or by the system itself, or maybe because of incorrect shutdown?

At the moment, I'm setting a new test system using Lucid. Does anybody know if this is a "common" error in Karmic? Hope someone can give me some comments or ideas to try.

Thanks in advance for any comment.

---

### Post by SeijiSensei on 2010-10-16
What filesystem are you using?  Have you tried both ext3 and ext4?

I haven't used Karmic in quite a while now, but I don't recall encountering that problem when I did.  If this is going to be a production release, I'd move to Lucid since that's a "long-term-support" version.

---

### Post by GeoMX on 2010-10-16
Thanks a lot for your comments SeijiSensei.

I've only tested ext4, what I'm planning is to create a test system using Karmic/ext3 and some others with Lucid/ext4. You're right, I was planning the move to Lucid because of the LTS, it's just that previous developer was working with Karmic and I thought switching to Lucid would take some more testing time.

---

### Post by GeoMX on 2010-10-20
Well, the ext3 with Karmic version has started the testing process. Meanwhile, I'm setting up a new version using Lucid :).
I'll try to update this discussion when I have some results.

---

