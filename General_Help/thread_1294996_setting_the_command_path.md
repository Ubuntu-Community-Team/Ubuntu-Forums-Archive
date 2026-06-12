---
title: "setting the command path"
date: 2009-10-18
forum: General Help
---

### Post by shariefbe on 2009-10-18
hi friends,
    I am using ubuntu 8.10..In that i tried one command. But it says the following error..

```

bash: emulator: command not found

```
This command is used in android development.
i think i have to set the path. But i dont know how to set the path. This is the list of /bin
```

sharief@sharief-desktop:/bin$ ls
bash                  dnsdomainname  mountpoint      sleep
bunzip2               dumpkeys       mt              stty
bzcat                 echo           mt-gnu          su
bzcmp                 ed             mv              sync
bzdiff                egrep          nano            tailf
bzegrep               false          nc              tar
bzexe                 fgconsole      nc.traditional  tempfile
bzfgrep               fgrep          netcat          touch
bzgrep                fuser          netstat         true
bzip2                 fusermount     ntfs-3g         ulockmgr_server
bzip2recover          grep           ntfs-3g.probe   umount
bzless                gunzip         open            uname
bzmore                gzexe          openvt          uncompress
cat                   gzip           pidof           unicode_start
chgrp                 hostname       ping            vdir
chmod                 ip             ping6           which
chown                 kbd_mode       ps              zcat
chvt                  kill           pwd             zcmp
cp                    ld_static      rbash           zdiff
cpio                  ln             readlink        zegrep
dash                  loadkeys       rm              zfgrep
date                  login          rmdir           zforce
dbus-cleanup-sockets  ls             rnano           zgrep
dbus-daemon           lsmod          run-parts       zless
dbus-uuidgen          mkdir          sed             zmore
dd                    mknod          setfont         znew
df                    mktemp         setupcon
dir                   more           sh
dmesg                 mount          sh.distrib
sharief@sharief-desktop:/bin$ 

```

can anyone help me how to set this command in this path?

---

### Post by Johnny B on 2009-10-18
you have to install "emulator" first
although its not in the repos under that name.

to find where a command is installed use
> which [command name]

---

### Post by shariefbe on 2009-10-19
i am not getting any o/p for this command...

---

### Post by shariefbe on 2009-10-19
i dont know what to do to set the path. i tried but it seems wrong
```

sharief@sharief-desktop:~$ export PATH-$PATH:/home/sharief/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools/emulator
bash: export: `PATH-/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/sharief/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools/emulator': not a valid identifier
sharief@sharief-desktop:~$ 
```

Can anyone help me

---

### Post by shariefbe on 2009-10-20
oh...Again i am having thus problem for other command..

```

sharief@sharief-desktop:~/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools$ export PATH=$PATH:/home/sharief/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools/android 

```

i think this is correct to set the apth. But i dont know wht its not working

oh...Again i am having thus problem for other command..
```

bash: android: command not found

```

---

### Post by snova on 2009-10-20
> **shariefbe said:**
> ```

sharief@sharief-desktop:~/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools$ export PATH=$PATH:/home/sharief/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools/android 

```

Is ~/.../tools/android a directory or the program itself? $PATH is a list of directories to search through, you wouldn't add the name of the executable to it.

I think this should work:

```

export PATH=$PATH:~/Desktop/SDK/android-sdk-linux_x86-1.5_r3/tools

```

And perhaps add that line to the end of your ~/.bashrc file so you don't have to do it again...

---

