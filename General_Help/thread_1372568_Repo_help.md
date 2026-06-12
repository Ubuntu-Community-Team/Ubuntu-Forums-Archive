---
title: "Repo help"
date: 2010-01-04
forum: General Help
---

### Post by bluestar14 on 2010-01-04
i followed all the instructions at: [HTML]http://source.android.com/download[/HTML]under installing repo, but when i try to do repo init command in mydroid, it says, command repo not found, using ubuntu 9.10     :frown:

---

### Post by Leppie on 2010-01-04
did you install the repo script?
from the android page:
> Installing Repo 

$ curl [http://android.git.kernel.org/repo](http://android.git.kernel.org/repo) >~/bin/repo
$ chmod a+x ~/bin/repo
$ mkdir working-directory-name
$ cd working-directory-name
$ repo init -u git://android.git.kernel.org/platform/manifest.gi

it might help reading the instructions provided on the websites... ;)

---

### Post by bluestar14 on 2010-01-04
thats what i did..

---

### Post by bluestar14 on 2010-01-04
also, i have installed everything needed

---

### Post by Leppie on 2010-01-04
what is the output of the following command:
```
$whereis repo
```

---

### Post by bluestar14 on 2010-01-04
here it is:
```
avin@STUDYROOML:~$ whereis repo
repo:
```

---

### Post by Leppie on 2010-01-04
sorry, try this command:
```
sudo find / -name repo
```

---

### Post by bluestar14 on 2010-01-04
its taking a while.....

---

### Post by bluestar14 on 2010-01-04
here it is:
```
avin@STUDYROOML:~$ sudo find / -name repo
[sudo] password for avin: 
/home/avin/bin/repo

```

---

### Post by Leppie on 2010-01-04
you need to add the repo folder to the path, or just use the complete path:
```
$~/bin/repo
```

to add the folder to your path:
```
gksudo avin gedit ~/.bashrc
```
add the following line to the end of the file and save:
```
export PATH=$PATH:/home/avin/bin
``` 

you will have to logout and login again, or restart your xwindows session (Ctrl+Alt+Backspace in terminal)

---

### Post by bluestar14 on 2010-01-04
i tried first command, but it says "no such file or directory"y, there isn't any repo folder, only a script

---

### Post by smo0th on 2010-01-04
that last should work..

---

### Post by Leppie on 2010-01-04
> **bluestar14 said:**
> i tried first command, but it says "no such file or directory"y, there isn't any repo folder, only a script
the "repo folder" is ~/bin

---

### Post by bluestar14 on 2010-01-04
ohok, so i will try $~/bin/

---

### Post by bluestar14 on 2010-01-04
when i do gksudo command, it asks for password, and nothing happens

---

### Post by Leppie on 2010-01-04
then just open .bashrc from within gedit (or whatever editor you prefer).

---

### Post by bluestar14 on 2010-01-04
so i just paste it right under "fi"?

---

### Post by Leppie on 2010-01-04
yes, you can just put it after the last line.
mind you, the file should end in an empty line ;)

---

### Post by bluestar14 on 2010-01-04
ok, did it all, but it still doesn't work, here is output:
```
avin@STUDYROOML:~/mydroid$ repo init -u git://android.git.kernel.org/platform/manifest.gi
gpg: keyring `/home/avin/.repoconfig/gnupg/secring.gpg' created
gpg: keyring `/home/avin/.repoconfig/gnupg/pubring.gpg' created
gpg: /home/avin/.repoconfig/gnupg/trustdb.gpg: trustdb created
gpg: key 920F5C65: public key "Repo Maintainer <repo@android.kernel.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1

Getting repo ...
   from git://android.git.kernel.org/tools/repo.git
remote: Counting objects: 958, done.
remote: Compressing objects: 100% (382/382), done.
remote: Total 958 (delta 600), reused 894 (delta 556)
Receiving objects: 100% (958/958), 285.21 KiB | 295 KiB/s, done.
Resolving deltas: 100% (600/600), done.
From git://android.git.kernel.org/tools/repo
 * [new branch]      master     -> origin/master
 * [new branch]      stable     -> origin/stable
 * [new tag]         v1.6.8.10  -> v1.6.8.10
From git://android.git.kernel.org/tools/repo
 * [new tag]         v1.0       -> v1.0
 * [new tag]         v1.0.1     -> v1.0.1
 * [new tag]         v1.0.2     -> v1.0.2
 * [new tag]         v1.0.3     -> v1.0.3
 * [new tag]         v1.0.4     -> v1.0.4
 * [new tag]         v1.0.5     -> v1.0.5
 * [new tag]         v1.0.6     -> v1.0.6
 * [new tag]         v1.0.7     -> v1.0.7
 * [new tag]         v1.0.8     -> v1.0.8
 * [new tag]         v1.0.9     -> v1.0.9
 * [new tag]         v1.1       -> v1.1
 * [new tag]         v1.2       -> v1.2
 * [new tag]         v1.3       -> v1.3
 * [new tag]         v1.3.1     -> v1.3.1
 * [new tag]         v1.3.2     -> v1.3.2
 * [new tag]         v1.4       -> v1.4
 * [new tag]         v1.4.1     -> v1.4.1
 * [new tag]         v1.4.2     -> v1.4.2
 * [new tag]         v1.4.3     -> v1.4.3
 * [new tag]         v1.4.4     -> v1.4.4
 * [new tag]         v1.5       -> v1.5
 * [new tag]         v1.5.1     -> v1.5.1
 * [new tag]         v1.6       -> v1.6
 * [new tag]         v1.6.1     -> v1.6.1
 * [new tag]         v1.6.2     -> v1.6.2
 * [new tag]         v1.6.3     -> v1.6.3
 * [new tag]         v1.6.4     -> v1.6.4
 * [new tag]         v1.6.5     -> v1.6.5
 * [new tag]         v1.6.6     -> v1.6.6
 * [new tag]         v1.6.7     -> v1.6.7
 * [new tag]         v1.6.7.1   -> v1.6.7.1
 * [new tag]         v1.6.7.2   -> v1.6.7.2
 * [new tag]         v1.6.7.3   -> v1.6.7.3
 * [new tag]         v1.6.7.4   -> v1.6.7.4
 * [new tag]         v1.6.7.5   -> v1.6.7.5
 * [new tag]         v1.6.8     -> v1.6.8
 * [new tag]         v1.6.8.1   -> v1.6.8.1
 * [new tag]         v1.6.8.2   -> v1.6.8.2
 * [new tag]         v1.6.8.3   -> v1.6.8.3
 * [new tag]         v1.6.8.4   -> v1.6.8.4
 * [new tag]         v1.6.8.5   -> v1.6.8.5
 * [new tag]         v1.6.8.6   -> v1.6.8.6
 * [new tag]         v1.6.8.7   -> v1.6.8.7
 * [new tag]         v1.6.8.8   -> v1.6.8.8
 * [new tag]         v1.6.8.9   -> v1.6.8.9
Getting manifest ...
   from git://android.git.kernel.org/platform/manifest.gi
fatal: The remote end hung up unexpectedly
fatal: cannot obtain manifest git://android.git.kernel.org/platform/manifest.gi
avin@STUDYROOML:~/mydroid$ repo init -u git://android.git.kernel.org/platform/manifest.git
Traceback (most recent call last):
  File "/home/avin/mydroid/.repo/repo/main.py", line 235, in <module>
    _Main(sys.argv[1:])
  File "/home/avin/mydroid/.repo/repo/main.py", line 217, in _Main
    repo._Run(argv)
  File "/home/avin/mydroid/.repo/repo/main.py", line 123, in _Run
    cmd.Execute(copts, cargs)
  File "/home/avin/mydroid/.repo/repo/subcmds/init.py", line 218, in Execute
    self._SyncManifest(opt)
  File "/home/avin/mydroid/.repo/repo/subcmds/init.py", line 110, in _SyncManifest
    m.PreSync()
  File "/home/avin/mydroid/.repo/repo/project.py", line 1440, in PreSync
    cb = self.CurrentBranch
  File "/home/avin/mydroid/.repo/repo/project.py", line 271, in CurrentBranch
    b = self.work_git.GetHead()
  File "/home/avin/mydroid/.repo/repo/project.py", line 1226, in GetHead
    fd = open(path, 'rb')
IOError: [Errno 2] No such file or directory: '/home/avin/mydroid/.repo/manifests/.git/HEAD'
```

---

### Post by bluestar14 on 2010-01-04
i retried running it, thats why command is run twice, maybe that has something to do with it?

---

### Post by bluestar14 on 2010-01-04
wait, never mind, i just deleted mydroid and remade it, ran command again, and it worked!! Thank you very much!

---

