---
title: "Unionfs-fuse issues"
date: 2009-10-29
forum: General Help
---

### Post by Jayferd on 2009-10-29
I'm running Karmic on an Eeepc with a 4G hard drive.  I'm trying to do this: 

[http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/)

It's a combination of squashfs and unionfs to reduce the size of /usr on the hdd.  Unfortunately, unionfs-tools is no longer in the repos, only unionfs-fuse.  So here's what I tried.

I've got a folder called /.filesystems/usr which contains my squashfs archive usr.sqfs, and two folders "persist" and "overlay".  My fstab looked like this (it got nuked somehow--long story--so I had to rewrite it):

```

#fstab

#<resource> <mount point> <type> <options> <dump> <other thing>

#main hdd
/dev/sda1   /             ext4   defaults   0      0

#swap
/dev/sda    none          swap    sw        0      0

#squashfs
/.filesystems/usr/usr.sqfs /.filesystems/usr/persist squashfs loop 0 0

#unionfs
unionfs-fuse#/.filesystems/usr/overlay=rw:/.filesystems/usr/persist=ro /usr fuse cow,nodev,noatime 0 0

#end fstab

```

Since it turned out that the unionfs-fuse binary is *in* /usr, I copied the binary to /.filesystems and changed "unionfs-fuse" in the unionfs line to "/.filesystems/unionfs-fuse".  When I rebooted into recovery mode, it mounted fine.  The /usr directory contained the contents of the squashfs archive and the one or two dummy files I'd put in the overlay.

But it still won't boot normally.  It hangs at the splash screen and then leaves me with a "busy" mouse over a blank screen.  To experiment with why this might be happening, I typed "init 5" from the root terminal in recovery mode.  It prompts me for my username and login, and then gives me a user terminal.  What's weird is that I can poke around the filesystem, but when I try to ls /usr, I get "Permission Denied".  The obvious effect of this is that I can't run most commands, including sudo.  What's weirder is that according to my root terminal, the permissions on all the folders in /usr are 755, so they should be publicly readable.

This has been a real learning experience so far, and I'm at a point where my searches and research are getting stale.  I'd like just need to be pointed in the right direction.

---

### Post by Jayferd on 2009-10-29
...bump.

If someone can point me in the direction of something that would provide the functionality of the old unionfs-tools package, that would be awesome.  The docs are all pretty vague on this.

---

### Post by Jayferd on 2009-10-31
Bump again.  I've switched to aufs, which refuses to work entirely.  At this point the thing wipes my fstab every time I try to boot into recovery mode.  Help please!

---

### Post by Turpin on 2010-02-13
bump this motha.  :P
I want to compress my /usr, but the karmic koala has me by the throat.  It's vicious, maybe rabid.  I so miss the jackelope.  Will the ibis save me?

---

### Post by falconindy on 2010-02-13
While I hate to support a necroed thread, you shouldn't be using UnionFS -- it's old and crusty. use Aufs2 instead.

This'll get you started.
[http://forums.gentoo.org/viewtopic-p-4732709.html#4732709](http://forums.gentoo.org/viewtopic-p-4732709.html#4732709)

---

### Post by Turpin on 2010-02-14
That's an amazing coincidence.  I just found that and it worked.  Until... I installed aufstools.  You see, I forgot to install them because the partition backup I restored to didn't have them installed yet.  But those instructions got the system up and running.  But I don't know how because aufstools, in fact aufs..anything, wasn't installed prior to it working.  And after I installed them, my system won't even let me login.  What I DO have installed is unionfs-fuse.  I'm thinking of trying it again and then uninstalling unionfstools, see if it reboots, then install aufstools again if it does boot.  What I think may be happening is, even though aufs is the mount type in fstab, it's using unionfs-fuse instead because that's the closest thing to aufs that it has installed.  By the way, I've been trying nearly this same procedure with aufs that I've found in other threads, except I remembered to install aufstools in the early steps and it keeps coming up with the same bad result, crashing at disk mounting, not even letting me login at terminal.  I don't doubt that aufs is probably better in speed, but I'll make this work in whatever way I must.  unionfs has always been plenty fast for my usr compression needs in the past, and while I had it working, I noticed no slowdown whatsoever.

---

### Post by falconindy on 2010-02-14
I use squash and aufs to make incremental backups. While I have no basis for comparison, it's "pretty fast", and it rarely gives me any problems.

---

### Post by Turpin on 2010-02-14
I finally found my way back here.  Here is what I've found: the link that you referred me to as a starter does indeed work.  I had found it shortly before you gave it to me, but thanks for helping and affirming I was on the right track.  What is weird is, it works without either aufs-tools or unionfstools/unionfs-fuse being installed.  In fact it DOESN't work if aufstools is installed, which makes no sense to me at all.  But, who am I to argue?  I just wanted it to work, so that's what I got I guess.  I wonder.. does anyone know why it would stop working as it does when aufstools is installed?

I should probably run down the list of exactly what I did and didn't do.  I did install squashfs-tools, but I didn't install aufs-tools.  As mentioned, the times that I've tried with them installed, the file system doesn't mount. I created /squashed/usr/ro and /squashed/usr/rw.  Ran  sudo mksquashfs /usr /squashed/usr/usr.sfs -b 65536   to create the compressed filesystem.  I put the lines into my /etc/fstab directly underneath the line for the / partition.
/squashed/usr/usr.sfs   /squashed/usr/ro   squashfs   loop,ro   0 0
usr    /usr    aufs    udba=reval,br:/squashed/usr/rw:/squashed/usr/ro  0 0
Then I rebooted into Puppy Linux live usb, mounted my sda1, renamed /usr to /usr-old and made a new empty /usr folder.  Rebooted and it works.

I didn't bother with step 8 because right now I'm more concerned with mounting than dismounting and there doesn't seem to be any delays or hangups so far, so I take it Ubuntu's normal dismount scripts are already doing a good job of dismounting without any extra coercion. I've verified that it is properly maintaining the overlay.  Changes I make in subfolders of /usr persist after reboot and show up in the /squashed/usr/rw folder as they should. It's working!  :)  All this excitement for having saved 1 GB..  When you only have a 4GB HD, the little things seem bigger.  :P

So there it is.  It seems like this procedure should work only if one has installed aufs-tools, yet exactly the opposite is true.  It's a mystery to me.  This is under karmic by the way.  I think jaunty has less problems with this kind of thing because it doesn't try to break rules to boot up faster like karmic is said to.  I do like the fast karmic boot time though, and now that I have this working, it's all the sweeter.

---

### Post by aakef on 2010-04-03
falconindy: unionfs-fuse old and crusty? Please don't confuse it with unionfs.

Jayferd: I think I will create another upload to mentors moving the binary to /bin.
Also, please check out out /usr/share/doc/unionfs-fuse/examples/unionfs-fuse-nfs-root, there are options given you will need:

-o default_permissions,allow_other,use_ino,nonempty,suid,cow,max_files=16000

If something does not work, the optimal way is to write to the mailing list ( 
[email]unionfs-fuse@googlegroups.com[/email])


Cheers,
Bernd

---

### Post by halfvulcan on 2010-04-08
> **Turpin said:**
> bump this motha.  :P
I want to compress my /usr, but the karmic koala has me by the throat.  It's vicious, maybe rabid.  I so miss the jackelope.  Will the ibis save me?
Oops.  That was supposed to be "will the lynx save me."  It makes one reconsider one's own lacking attempts at humour when one must correct such ridiculous statements by oneself.

---

