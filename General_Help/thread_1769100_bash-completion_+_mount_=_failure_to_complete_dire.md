---
title: "bash-completion + mount = failure to complete directories"
date: 2011-05-27
forum: General Help
---

### Post by JohnFH on 2011-05-27
I've spent some time searching for answers to this and I haven't found much at all.  Please feel free to post pointers to other threads that discuss this particular problem, if you find any.

The problem is that in bash I want to mount an iso file to inspect the contents with the command:
```
sudo mount myCD.iso CDMount -o loop
```

The command works fine, but pressing tab to complete either the iso filename or the CDMount directory does not work.  The completion suggestions I get are existing mountpoints which is completely unhelpful.  The completion suggestions should include the files and directories in the current directory.  This worked with Ubuntu 10.04 and not with 11.04.

Has anyone else seen this?  How did you solve or get round it?

Thanks,
John.

---

### Post by JohnFH on 2011-05-31
No response whatsoever?  Quite a few times now my support questions have been met with a wall of silence.  The support on these forums is quite poor I have to say.  Disappointing.

---

### Post by Lekensteyn on 2011-12-05
Ubuntu changed the completion scripts in order to be "more smart". That is, it completes entries from /etc/fstab only. Now, not everyone puts mount points in /etc/fstab and it's just annoying that I cannot complete from /dev/disk/by-label anymore nor loop mounts of .iso files.

To revert to the old behavior, edit /etc/bash_completion.d/mount and change:
```
complete -F _mount -o default -o dirnames mount
```
to:
```
complete -F _longopt -o filenames mount
```

By doing so, you loose the completions of /etc/fstab, but at least it allows you to complete files and directories.

---

