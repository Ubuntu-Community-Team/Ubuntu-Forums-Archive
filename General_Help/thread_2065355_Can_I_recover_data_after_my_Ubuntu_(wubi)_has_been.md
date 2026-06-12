---
title: "Can I recover data after my Ubuntu (wubi) has been uninstalled?"
date: 2012-10-01
forum: General Help
---

### Post by Archaeologik on 2012-10-01
I was running Ubuntu 11.04 through Wubi on my PC and I decided that since I don't use it all that often i would simply get rid of it. I (thought I had) put all of the files that I needed onto an external hard-drive and then went ahead with the uninstall. I realized only afterward that some very, and I mean very, important data was left off of the external harddrive and was likely wiped out when i uninstalled Wubi. Is that data still on my computer somewhere? Can I get access to it through windows? Help!

---

### Post by houseworkshy on 2012-10-01
I don't know but as much for an excuse to bump as anything else do know of some distros which may help.  There are quite a few of them and this is a good place to look [http://distrowatch.com/search.php](http://distrowatch.com/search.php)  You'll want "recovery" and ideally "live medium".  Then look at the spec's of individual that search pulls up and make sure that the distros can handle the involved file systems ( most will handle all of them).  I haven't had to use this sort of thing for a long time so can't give a specific recomendation as to which is the best one currently.  
The files you are looking for will almost certainly ( I'm not an expert on wubi installs either ) be in /home/username when you get it back, "username" being whatever user name you used on the install.
Not amazingly helpful I know but having lost data several times in pre-linux days know how horrid it is, data is more important than operating systems because it can't be replaced.
Good luck and bump.

---

### Post by bcbc on 2012-10-01
> **Archaeologik said:**
> I was running Ubuntu 11.04 through Wubi on my PC and I decided that since I don't use it all that often i would simply get rid of it. I (thought I had) put all of the files that I needed onto an external hard-drive and then went ahead with the uninstall. I realized only afterward that some very, and I mean very, important data was left off of the external harddrive and was likely wiped out when i uninstalled Wubi. Is that data still on my computer somewhere? Can I get access to it through windows? Help!

No. When you uninstall Wubi it deletes the \ubuntu directory that contains the virtual disk (root.disk). So it's gone.

Now in theory the root.disk is just a file that's been deleted, so if you run testdisk you might be able to undelete it. But I think that because of it's size and the fact that it's often not contiguous might make this difficult. Also, if you've been using your computer since uninstalling, then it may have reused parts o the space taken up by the root.disk.

So, that's something you can try. 

There may be other things you can do... e.g photorec is supposed to be able to recover data files from any medium (even damaged file systems or ones that have been reformatted). So that's another approach, but be prepared for a long recovery and the hours of sifting through the results. I don't know how this would work with the virtual filesystem containing files within it...

Maybe other people have better ideas.

---

### Post by houseworkshy on 2012-10-01
Good points.  I should have mentioned that, when doing a recovery it is important to run the recovery program from another drive, so use a live distro in the cd/dvd drive for that.  It is also important to dump the data on some drive other than the one you are trying to recover, your external hd perhaps.  And yes don't use the drive with the lost data on it, deletes aren't really deletes, just space being marked as useable, but once marked new activity can overwrite those areas.  Don't despair though, there are some very powerful data recovery tools around.

---

