---
title: "Using Grsync to backup /root partition .."
date: 2012-02-20
forum: General Help
---

### Post by dragonfly41 on 2012-02-20
I have my ubuntu 10.10 in a dual boot configuration ..,,

/dev/sda7   contains ubuntu /root
/dev/sda8   contains ubuntu /home

I have hit problems in ubuntu so I'm about to repair (not reformat)
these two partitions

I'm warned to backup the systems files first.

I tried clonezilla to clone the root partition into  spare ext4 partition on a USB device. 

But although I had plenty of space in the target partition the actual size of the target partition was smaller than the source partition.

This resulted in a failed cloning and the target partition later showed as "unknown" when viewed in partition editor and target partition had to be reformatted.

I decided then to try Grsync GUI.

I setup the source and target partitions in Grsync GUI.

Then I started with a dry run to test the sync (since there is 7 GB to backup).

First point I noted was lots of messages saying .. skipping non-regular file .. 

```

skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/initrd.img"
skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/initrd.img.old"
skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/vmlinuz"
skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/vmlinuz.old"

and so on .......


```There were other blocks showing that a sync was taking place without errors ..

```

8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/netstat
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/nisdomainname
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/ntfs-3g
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/ntfs-3g.probe
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/ntfs-3g.secaudit
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/ntfs-3g.usermap

```I stopped the dry run after a few minutes and looked at the error log ..

Error list:

```

[COLOR=Red]rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/.Trash-0" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/.kde" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/etc/chatscripts" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/etc/cups/ssl" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/etc/ppp/peers" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/etc/ssl/private" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/lost+found" failed: Permission denied (13)
rsync: opendir "/media/8eeb2f0d-92c7-463e-8961-3a1241fc148a/root" failed: Permission denied (13)
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(541) [sender=3.0.7]
rsync: writefd_unbuffered failed to write 78 bytes to socket [generator]: Broken pipe (32)
Rsync process exit status: 20[/COLOR]

```Is it worth carrying on to do a full rsync with about 7GB in /root partition to backup?

What might be causing these errors?

//==========================================

**[COLOR=Red][Later Edit][/COLOR]**

I realised I needed to launch Grsync using command [COLOR=Navy]**gksudo Grsync**[/COLOR] to operate with root permissions.

That allowed the dry run to complete but there are still messages "skipping non-regular file"

such as these ..

```

skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/initrd.img"
skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/initrd.img.old"
skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/vmlinuz"
skipping non-regular file "8eeb2f0d-92c7-463e-8961-3a1241fc148a/vmlinuz.old"

and more throughout the run ..


8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/busybox
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzcat
[COLOR=Red]skipping non-regular file[/COLOR] "8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzcmp"
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzdiff
[COLOR=Red]skipping non-regular file [/COLOR]"8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzegrep"
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzexe
[COLOR=Red]skipping non-regular file[/COLOR] "8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzfgrep"
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzgrep
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzip2
8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzip2recover
[COLOR=Red]skipping non-regular file[/COLOR] "8eeb2f0d-92c7-463e-8961-3a1241fc148a/bin/bzless"


```
[B][COLOR=Red]
[Further Edit][/COLOR][/B]

Found just one thread on this topic.

[http://ubuntuforums.org/showthread.php?t=1256193&highlight=skipping+non-regular+file](http://ubuntuforums.org/showthread.php?t=1256193&highlight=skipping+non-regular+file)


[B][COLOR=Red][Further Edit]
[COLOR=Black]
[/COLOR][/COLOR][/B][COLOR=Black]I think this article might point to an answer my question [/COLOR][B][COLOR=Red]
[/COLOR][/B]
[http://ss64.com/bash/rsync.html](http://ss64.com/bash/rsync.html)

so in in Grsync Advanced Options I ticked .. Copy symlinks as symlinks

and in Grsync Extra Options I ticked .. Run as superuser

this seemed to lose the error messages in the dry run ..

[COLOR=Navy]SYMBOLIC LINKS

Three basic behaviours are possible when rsync encounters a symbolic link in
the source directory.

By default, symbolic links are not transferred at all.
[/COLOR][COLOR=Navy][COLOR=Red]A message "skipping non-regular" file is emitted[/COLOR] for any symlinks that exist.

If --links is specified, then symlinks are recreated with the same target
on the destination. Note that --archive implies --links.

If --copy-links is specified, then symlinks are "collapsed" by copying their referent,
rather than the symlink.[/COLOR]

---

