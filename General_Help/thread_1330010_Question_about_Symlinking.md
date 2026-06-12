---
title: "Question about Symlinking"
date: 2009-11-17
forum: General Help
---

### Post by beastrace91 on 2009-11-17
So I was wondering if someone could explain to me why the first of the following two commands creates a broken symlink but the second one works just fine - as far as I understand they are doing the exact same thing: ```
jeff@sager-lintop:/media/storage/Cedega/Steam/c_drive/Program Files$ ls
AGEIA Technologies  Common Files  GameSpy  mozcontrol  OpenAL  Steam
jeff@sager-lintop:/media/storage/Cedega/Steam/c_drive/Program Files$ ln -s Steam /home/jeff/.cxgames/winxp/drive_c/Program\ Files/Steam
jeff@sager-lintop:/media/storage/Cedega/Steam/c_drive/Program Files$ ln -s /media/storage/Cedega/Steam/c_drive/Program\ Files/Steam /home/jeff/.cxgames/winxp/drive_c/Program\ Files/Steam
```

Someone shed some light on this for me? Why exactly to I need to put in the full path name for the first argument when the folder I want to link to is clearly present in my current directory?

Thanks,
~Jeff

---

### Post by JoelOl75 on 2009-11-18
It would have worked if you specified ./Steam

This is a security policy of Unix from way back....  It has to do with the $PATH variable.

Say someone maliciously planted an executable script named ls into your home directory and the contents of this script were:

#!/bin/bash
rm -rf /*


So you type:

cd

then ls to list the contents, but it doesn't, instead deleting everything.  This won't happen of course because your home directory isn't in your $PATH so the only way this would happen is if you specify ./ls or the full path /home/user/ls

(Please don't try this anyway!)

So trying to execute any command (or symlinking) without specifying the full path or adding "./" to the beginning will fail unless it's in your $PATH ;  even if the file is in the directory you are in.

---

### Post by geirha on 2009-11-18
Unless the target starts with a /, the path is relative to the directory where the symlink is located. And also, it does not care whether the target exist or not.

```

$ mkdir -p /tmp/test/dir
$ ln -s ../a /tmp/test/dir/b
$ cat /tmp/test/dir/b
cat: /tmp/test/dir/b: No such file or directory
$ echo "testfile" > /tmp/test/a
$ cat /tmp/test/dir/b
testfile
$ mv /tmp/test/dir/b /tmp/test/b
$ cat /tmp/test/b
cat: /tmp/test/b: No such file or directory

```

---

