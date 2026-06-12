---
title: "/bin/ln --force does not force?"
date: 2011-04-17
forum: General Help
---

### Post by Mozai on 2011-04-17
So, the man page for 'ln' says that '--force' will remove the destination file before performing it's operation.  Looks like it's not doing what it's supposed to.

```
deunan:~/.minecraft$ ls -ld bin bin.modded
lrwxrwxrwx 1 moses moses   16 2011-04-17 14:40 bin -> bin.worldrecord/
drwxr-xr-x 3 moses moses 4096 2011-04-17 14:54 bin.modded
deunan:~/.minecraft$ /bin/ln -s bin.modded bin || echo NOPE
/bin/ln: creating symbolic link `bin/bin.modded': File exists
NOPE
deunan:~/.minecraft$ /bin/ln --force -s bin.modded bin || echo NOPE
deunan:~/.minecraft$ ls -ld bin
lrwxrwxrwx 1 moses moses 16 2011-04-17 14:40 bin -> bin.worldrecord/

deunan:~/.minecraft$ apt-cache policy $(dpkg -S $(which ln))
coreutils:
  Installed: 8.5-1ubuntu6
```

What'm I doing wrong here?  I've used 'ln -sf real_dir softlink_name' to delete and replace softlinks before, but now '--force' isn't removing the destination AND /bin/ln is returning exit code 0 instead of telling me it failed to make the link.

(Don't say "just rm it first LOL"; that is *not* the point of this question.)

---

### Post by marshmallow1304 on 2011-04-18
It's because bin.worldrecord/ is a directory.  When you run
```
ln -s bin.modded bin
```
the first time, ln is dereferencing the existing link and reading this as
```
ln -s bin.modded bin.worldrecord/
```

This causes ln to run with the 3rd form (see man page) and it creates bin.worldrecord/bin.modded which is a symbolic link in a loop.  When you run ln again with --force, it removes bin.worldwide/bin.modded and replaces it with an identical copy.

Here's an example:
```
$ mkdir bin.worldrecord
$ touch bin.modded
$ ln -s bin.worldrecord/ bin
$ ls -ld bin bin.modded
lrwxrwxrwx 1 benntoo benntoo 16 Apr 18 00:45 bin -> bin.worldrecord/
-rw-r--r-- 1 benntoo benntoo  0 Apr 18 00:44 bin.modded
$ ls bin.worldrecord/
$ ln -s bin.modded bin
ls -ld bin.worldrecord/
total 0
lrwxrwxrwx 1 benntoo benntoo 10 Apr 18 00:45 bin.modded -> bin.modded
$ file bin.worldrecord/bin.modded 
bin.worldrecord/bin.modded: symbolic link in a loop
$ ln -s bin.modded bin
ln: failed to create symbolic link `bin/bin.modded': File exists
```


To do this the proper way, use the -n switch (--no-dereference) with --force when overwriting a symlink to a directory:
```
$ ls -ld bin bin.modded
lrwxrwxrwx 1 benntoo benntoo 16 Apr 18 01:00 bin -> bin.worldrecord/
-rw-r--r-- 1 benntoo benntoo  0 Apr 18 01:00 bin.modded
$ ln -sn bin.modded bin
ln: failed to create symbolic link `bin': File exists
$ ln -snf bin.modded bin
$ ls -ld bin bin.modded
lrwxrwxrwx 1 benntoo benntoo 10 Apr 18 01:01 bin -> bin.modded
-rw-r--r-- 1 benntoo benntoo  0 Apr 18 01:00 bin.modded
```

---

