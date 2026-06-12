---
title: "cat command not working"
date: 2011-05-22
forum: General Help
---

### Post by 9072997 on 2011-05-22
this is what i did


jon@Laptop:~$ echo hello world > out.txt
jon@Laptop:~$ ls
Desktop    Downloads         out.txt   Public      Videos
dev        examples.desktop  Pictures  Templates   VirtualBox VMs
Documents  Music             Projects  Ubuntu One
jon@Laptop:~$ cat out.txt
/home/jon/out.txt: No such file or directory
jon@Laptop:~$ 

so out.txt is their. i promise, but nothing. i can open it with nano though. any ideas? p.s i'm running ubuntu 10.10

---

### Post by Diametric on 2011-05-22
Hmmm....what are the permissions of said file? type this in the directory where the file is saved:

```
ls -larth
```and post the output, please.  Also, is there a chance that there are multiple users?

---

### Post by linuxinstalledfromhdd on 2011-05-22
try to chmod 777 out.txt

---

### Post by 9072997 on 2011-05-22
jon@Laptop:~$ echo hello world > out.txt
jon@Laptop:~$ ls -larth
total 1.2M
drwx------  4 jon jon 4.0K 2011-05-21 13:45 ..
drwxr-xr-x 56 jon jon 4.0K 2011-05-22 12:20 .
-rw-r--r--  1 jon jon   12 2011-05-22 12:26 out.txt
jon@Laptop:~$ chmod 777 out.txt
jon@Laptop:~$ cat out.txt
/home/jon/out.txt: No such file or directory

note: i shortened the output of ls -larth to remove irrelevant files and directories

---

### Post by CharlesA on 2011-05-22
Try using tab completion:
```
ls out [press tab]
```

---

### Post by 9072997 on 2011-05-22
```
jon@Laptop:~$ ls out [TAB]
.adobe/                       .mission-control/
.alienblaster_highscore       .mozilla/
.bash_history                 .mplayer/
.bash_logout                  Music/
.bashrc                       .nautilus/
.blender/                     out.txt
.byobu/                       .parallelrealities/
.cache/                       Pictures/
.chromium-bsu                 .pki/
.config/                      .profile
.dbus/                        .projectM/
Desktop/                      Projects/
dev/                          Public/
Documents/                    .pulse/
.dosbox/                      .pulse-cookie
Downloads/                    .qt/
.dvdcss/                      .recently-used.xbel
.esd_auth                     .recently-used.xbel.1BW3VV
.evolution/                   .recently-used.xbel.4CA4VV
examples.desktop              .recently-used.xbel.JJ2QVV
.filezilla/                   .recently-used.xbel.S28QVV
.fontconfig/                  .recently-used.xbel.WOCQVV
.FreeCAD/                     .recently-used.xbel.ZM04VV
jon@Laptop:~$ ls out 
.adobe/                       .mission-control/
.alienblaster_highscore       .mozilla/
.bash_history                 .mplayer/
.bash_logout                  Music/
.bashrc                       .nautilus/
.blender/                     out.txt
.byobu/                       .parallelrealities/
.cache/                       Pictures/
.chromium-bsu                 .pki/
.config/                      .profile
.dbus/                        .projectM/
Desktop/                      Projects/
dev/                          Public/
Documents/                    .pulse/
.dosbox/                      .pulse-cookie
Downloads/                    .qt/
.dvdcss/                      .recently-used.xbel
.esd_auth                     .recently-used.xbel.1BW3VV
.evolution/                   .recently-used.xbel.4CA4VV
examples.desktop              .recently-used.xbel.JJ2QVV
.filezilla/                   .recently-used.xbel.S28QVV
.fontconfig/                  .recently-used.xbel.WOCQVV
.FreeCAD/                     .recently-used.xbel.ZM04VV
.gconf/                       .screenrc
.gconfd/                      .ssh/
.gegl-0.0/                    .sudo_as_admin_successful
.gimp-2.6/                    Templates/
.gksu.lock                    .themes/
.gnome2/                      .thumbnails/
.gnome2_private/              .tlkgames/
.gnupg/                       Ubuntu One/
.gstreamer-0.10/              Videos/
.gtk-bookmarks                .VirtualBox/
.gvfs/                        VirtualBox VMs/
.ICEauthority                 .wings
.icons/                       .Xauthority
.kchmviewer/                  .xine/
.kde/                         .xscreensaver-getimage.cache
.libreoffice/                 .xsession-errors
.local/                       .xsession-errors.old
.macromedia/                  
jon@Laptop:~$ ls out out.txt
ls: cannot access out: No such file or directory
out.txt
jon@Laptop:~$ ls out
ls: cannot access out: No such file or directory
jon@Laptop:~$ ls out.txt
out.txt
jon@Laptop:~$
```

---

### Post by CharlesA on 2011-05-22
Hrm,

Try this:

```
ls -l out.txt
```

---

### Post by 9072997 on 2011-05-22
jon@Laptop:~$ echo hello world > out.txt
jon@Laptop:~$ ls -l out.txt
-rw-r--r-- 1 jon jon 12 2011-05-22 13:19 out.txt
jon@Laptop:~$ cat out.txt
/home/jon/out.txt: No such file or directory
jon@Laptop:~$ 

i just discovered that for some unknown reason /bin/cat works as expected, but the plain cat command does not. any idea why?

---

### Post by CharlesA on 2011-05-22
Do this:

```
sudo touch /forcefsck
```

Then reboot.

---

### Post by 9072997 on 2011-05-22
tried sudo touch /forcefsck, then rebooted. ubuntu checked all of my harddisks, but still only /bin/cat will work not plain cat

---

### Post by AlphaLexman on 2011-05-22
Do you have an alias for 'cat'?
```
unalias cat
```

Also,
```
which cat
```

---

### Post by SeijiSensei on 2011-05-22
What do you get if you run "echo $PATH"?  It sounds like you don't have /bin in your path.  The standard PATH is

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by Diametric on 2011-05-22
I hope the OP replies....was curious to see what the issue was - didn't even think about checking the $PATH - or the contents of /bin.

Cheers.

---

### Post by AlphaLexman on 2011-05-23
> **Diametric said:**
> I hope the OP replies....was curious to see what the issue was - didn't even think about checking the $PATH - or the contents of /bin.
I hope so too. I also did not think of the $PATH problem, but re-evaluating all the commands, SeijiSensei may have missed the fact that both 'ls' and 'touch' are executables in '/bin' and both commands seem to provide results the OP could post.

---

### Post by capscrew on 2011-05-23
> **AlphaLexman said:**
> I hope so too. I also did not think of the $PATH problem, but re-evaluating all the commands, SeijiSensei may have missed the fact that both 'ls' and 'touch' are executables in '/bin' and both commands seem to provide results the OP could post.

I was curious too.  There is only one cat (/bin/cat).  If the OP must use the absolute path then the $PATH is probably screwed up.  If there is an alias for cat then all bets are off.  :D

---

### Post by 9072997 on 2011-05-24
jon@Laptop:~$ unalias cat
bash: unalias: cat: not found
jon@Laptop:~$ which cat
/usr/bin/cat
jon@Laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
jon@Laptop:~$ 

i don't think that is the issue as when i run cat --help i receive the standard help message.

---

### Post by capscrew on 2011-05-24
> **9072997 said:**
> jon@Laptop:~$ unalias cat
bash: unalias: cat: not found
jon@Laptop:~$ which cat
/usr/bin/cat
jon@Laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
jon@Laptop:~$ 

i don't think that is the issue as when i run cat --help i receive the standard help message.

Interesting.  What distro of Linux are you using?   Here is what I get from my Ubuntu 10.04 LTS Desktop
```
$ whereis cat
cat: /bin/cat /usr/share/man/man1/cat.1.gz

```

The cat version is```
$ cat --version
cat (GNU coreutils) 7.4
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Torbjörn Granlund and Richard M. Stallman.

```

---

### Post by Diametric on 2011-05-24
Disregard - didn't see the reply to my earlier question, which the OP replied too.

My apologies.

---

### Post by AlphaLexman on 2011-05-24
Interesting that cat is in '/usr/bin' as well as '/bin'

However since '/usr/bin' is **before** '/bin' in your $PATH the shell uses the first one found.

Try this
```
sudo mv /usr/bin/cat /usr/bin/cat-old
```

Or,
```
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/bin:/sbin:/usr/bin:/usr/games'
```

CURIOUS, post the output
```
/usr/bin/cat --version
file /usr/bin/cat
```
Edit: Or use 'cat-old' if you moved/renamed as in my above example.

---

### Post by SecretCode on 2011-05-24
So far it seems that the problem is this /usr/bin/cat program, which is not part of a standard Ubuntu install. Because /usr/bin appears before /bin in $PATH, this one will take precedence. (Whereas /bin/cat has no problems, correct?)

What is your OS version? ```
uname -a
```

What is the size and version of this cat command?
```
ls -l /usr/bin/cat
```
```
/usr/bin/cat --version
```

:!: Maybe it comes from some other package.
```
dpkg --search /usr/bin/cat
```

---

### Post by SecretCode on 2011-05-24
Aside: if this was Windows, I'd say **you have a virus!** :o

---

### Post by 9072997 on 2011-05-25
jon@Laptop:~$ sudo mv /usr/bin/cat /usr/bin/cat-old
[sudo] password for jon:
jon@Laptop:~$ cat-old --version
fontconfig version 2.8.0
jon@Laptop:~$ uname -a
Linux Laptop 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
jon@Laptop:~$ ls -l /usr/bin/cat
ls: cannot access /usr/bin/cat: No such file or directory
jon@Laptop:~$ ls -l /usr/bin/cat-old
lrwxrwxrwx 1 root root 6 2011-05-17 17:34 /usr/bin/cat-old -> fc-cat
jon@Laptop:~$ dpkg --search /usr/bin/cat
dpkg: /usr/bin/cat not found.
jon@Laptop:~$ dpkg --search /usr/bin/cat-old
dpkg: /usr/bin/cat-old not found.

i run Ubuntu 10.10

it works now thank you so much

---

### Post by CharlesA on 2011-05-25
It seems that /usr/bin/cat-old is just a link to [fc-cat]("http://linux.die.net/man/1/fc-cat")

Very strange.

---

