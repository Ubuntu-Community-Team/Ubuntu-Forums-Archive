---
title: "rsync backing up across Samba and I don't want it to"
date: 2010-02-17
forum: General Help
---

### Post by jamesisin on 2010-02-17
I have written a script for backing up a /home tree.  The problem is that under that exists .gvfs/[myMusicServer] and its several hundred gigs of music.  Here is the script:

```
## Backup script for /home directory onto mounted drive

# check mount point (mount if necessary)

if ! mountpoint -q /media/MachinaMusica;
then
   mount /media/MachinaMusica
fi

# sync /home directory to mounted drive location (copy links; do not follow)

rsync -aSil --delete --progress /home /media/MachinaMusica/backups
```

What can I do to get it to ignore the network share (should it happen to be connected when the synk takes place)?

---

### Post by jamesisin on 2010-02-17
Hi.  Still hoping for a little assistance here.

---

### Post by mikewhatever on 2010-02-17
Not quite sure, but you could use the '--exclude=PATTERN' option with rsync.

--exclude=smb://something

---

### Post by jamesisin on 2010-02-17
Well, they are actually in the .gvfs folder (not the smb: distinction) so perhaps something like this:

```
rsync -aSil --delete --progress --exclude /home/[username]/.gvfs /home /media/MachinaMusica/backups
```

Or maybe my exclude should go after the backup part?

Is there a way to say all usernames?  In Windows I can often use %USERNAME%.

---

### Post by jamesisin on 2010-02-17
Forget that %USERNAME% question:

```
rsync -aSil --delete --progress --exclude /home/*/.gvfs /home /media/MachinaMusica/backups
```

How does that grab you?

---

### Post by mikewhatever on 2010-02-17
You can use $HOME instead of /home/username, other then that it should work.

---

### Post by jamesisin on 2010-02-18
Oh?  I thought $HOME was like ~ in that it meant "this particular user" and not "all users" (a la %USERNAME%).  I'll try that when I can test it.  The cron job spawning that script runs as root which has no /home so it should be easy enough to test.

Thanks, either way.

---

### Post by gmargo on 2010-02-18
Is your .gvfs/[myMusicServer] mounted via Samba, or exported by Samba?

If it is mounted via Samba, you can use the -x (or --one-file-system) option to not cross filesystem filesystem boundaries.  If it's just a regular directory, then one of the previously mentioned --exclude options should work.

---

### Post by jamesisin on 2010-02-18
> **gmargo said:**
> Is your .gvfs/[myMusicServer] mounted via Samba, or exported by Samba?

Excellent question.  How do I check and what's the difference?

---

### Post by jamesisin on 2010-02-18
Ok, so adding the x argument did the trick.

I would still be interested in knowing the difference (and how to make/test) as asked above if anyone can tell me.

---

### Post by gmargo on 2010-02-18
Type **mount** to see what filesystems are mounted.

---

### Post by jamesisin on 2010-02-18
So that gives me this:

```
$mount | grep gvfs
gvfs-fuse-daemon on /home/username/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=username)
```

---

### Post by jamesisin on 2010-02-22
The argument -l is implied by -a so I removed it:

```
rsync -aSi --delete --progress --exclude /home/*/.gvfs /home /media/MachinaMusica/backups
```

---

### Post by gmargo on 2010-02-22
You'll want to put quotes around the exclude pattern, to prevent the shell from expanding it.

Other rsync options I've used and you might like:

[LIST]
[*]--partial - to keep partially transmitted files
[*]--max-delete=10 - limits the number of deletions (preventing potential disaster)
[*]--dry-run - show what would happen, but don't do it
[/LIST]

---

### Post by jamesisin on 2010-02-22
But I do want the shell to expand the *.

Actually I changed it to $USER, but that also needs to be expanded.

What else can you tell me about the --partial argument?  How might that be useful?

---

### Post by gmargo on 2010-02-22
You want **rsync** to expand the pattern, not the shell.  Hence the quotes. You're copying files locally, but you can also use **rsync** to copy files from a remote host to the local host, and in that case the exclude pattern would apply to files on the remote host.

The **--partial** argument is especially useful when you are transfering large files over slow links.  If you interrupt the transfer for any reason, the partial download is not deleted.  When you restart **rsync**, it picks up where it left off, and avoids re-downloading that part.  (When you're backing up 500MB files over a slow link, it's a life saver! :P)

---

### Post by jamesisin on 2010-02-22
I can see how --partial could be useful.

I think you mean double quotes then:

```
rsync -aSi --delete --progress --exclude "/home/*/.gvfs" /home /media/MachinaMusica/backups
```

Suppose I were backing up a remote /home folder.  Would this exclude the local .gvfs folder or the remote .gvfs folder?

---

### Post by gmargo on 2010-02-22
Double quotes or single quotes will work in this case, but $USER will not - that's a user-specific local environment variable.  The pattern you had before should work.

```

rsync -aSi --delete --progress --exclude "/home/*/.gvfs" /home /media/MachinaMusica/backups

```> 
Suppose I were backing up a remote /home folder.  Would this exclude the  local .gvfs folder or the remote .gvfs folder?     
The syntax of **rsync** is essentially "rsync [options] source destination".  The --exclude option applies to the source side, which could be local or remote.  You should check out the rsync man page; there's quite a lot on filter rules and include/exclude patterns.

---

### Post by jamesisin on 2010-02-23
When I said this:

> Suppose I were backing up a remote /home folder. Would this exclude the local .gvfs folder or the remote .gvfs folder?

I was responding to this:

> You want rsync to expand the pattern, not the shell. Hence the quotes. You're copying files locally, but you can also use rsync to copy files from a remote host to the local host, and in that case the exclude pattern would apply to files on the remote host.

I think I would want this particular exclude pattern to take effect regardless of the location of the /home directory (local or remote) as I wouldn't want to then follow across a network share and add Samba shares to the copied /home backup.

> $USER will not - that's a user-specific local environment variable

Ah, I asked about that a few posts ago.  So $USER means "this current user" or "this specific user" and not "any user" or "* user" (as does the Windows variable %USERNAME%).

---

