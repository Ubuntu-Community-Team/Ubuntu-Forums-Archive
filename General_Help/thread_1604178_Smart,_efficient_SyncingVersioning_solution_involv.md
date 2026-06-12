---
title: "Smart, efficient Syncing/Versioning solution involving cloud storage"
date: 2010-10-23
forum: General Help
---

### Post by nosehat on 2010-10-23
Hi, and apologies in advance for a long post!  However, I imagine that this is a problem that many users face in one form or another.

Some background:  I have 4 computers I use regularly, at home, at work, and on the road.  3 of these computers run some variant of Ubuntu, and one of them runs Windows XP.  I have about 30GB of files I need to have access to.

My current solution for keeping this in sync is to have local copies of these files on all 4 machines, and a 5th copy of all the files in a Truecrypt volume on a 32GB USB flash drive.  (Truecrypt is necessary on the flash drive in case I physically lose it.)  I have Unison set up on all 4 machines to sync the flash drive files to the local files.

This system has its advantages--there's lots of redundancy, and there's data security at the weak link in the chain (the flash drive).  I can also mount the TC volume on the flash drive on any random XP machine (thanks to the portable TC .exe file), and work with my documents that way.

However, it's also rather cumbersome and time consuming on a day-to-day basis.  Mounting and unmounting the Truecrypt volume adds extra steps each time I move from one machine to another, and while Unison is lightning fast on Ubuntu, it can be really slow on the XP machine.

So my question is, what easier (automated) solutions exist for addressing syncing across multiple machines and platforms?  I'm considering Dropbox, but they seem to be plagued by very slow upload times, and checking/syncing all 30GB over the internet for 4 machines seems like it will be much slower than my current solution.

I should also note, I have access to a few GB of web storage as a WebDAV file system via my work.  I am able to mount this WebDAV system easily on all 4 of my machines, but there is not enough room on it for all my files.  

Is there a "smart" cloud syncing solution that only uses the cloud storage to store files that have changed, not the whole synced file structure, and then deletes the file from the cloud resource once the changed file has been propagated to all the synced machines?

Or is there some other type of solution I'm overlooking?

---

### Post by gyussz on 2010-10-23
Hey!

Ubuntu one is about to get a Windows client soon, and I think the plus storage is really cheap for it, and it's a great service imho. So if I were you I'd use Ubuntu One for the Ubuntu machines, and the pendrive until the Windows Client arrives. (If Ubuntu One is satisfying your needs :))

---

### Post by nosehat on 2010-10-23
Hi gyussz--

Thanks for your reply, and I can look again at Ubuntu One.  Unfortunately Canonical seems to be less forthcoming about the procedures they use to secure user data on the Ubuntu One servers than the Dropbox people are.

I guess I've got two basic problems with services like Dropbox and Ubuntu One:

1) Syncing *all* of my data to their server seems like it would be potentially quite slow.  Upload times seem to be a real problem for many Dropbox users, and I'm not sure how Canonical handles this.

2)  I'd really rather not use closed, proprietary software for something as mission-critical as maintaining my files, especially when there's no real reason to.  If the best solution is to rent 30MB of internet-accessible space somewhere and keep a full copy of everything there, I can do that myself with Unison.  But I was hoping for a "smarter" solution which could automate this and run on my own machine, like I outlined in my initial post.

---

