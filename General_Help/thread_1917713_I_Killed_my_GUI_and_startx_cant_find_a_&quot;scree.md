---
title: "I Killed my GUI and startx cant find a &quot;screen&quot;"
date: 2012-01-30
forum: General Help
---

### Post by GuyZerO on 2012-01-30
First off let me mention that this problem happened a while ago so i may have forgotten some of the details. A while ago I was trying to get used to backtrack5 and I was doing pretty well I think. I learned that you shouldn't be using root exclusively so i was creating a user account and trying to give it all the right  permissions and access.

I don't remember what did it specially but this is part of the error message i'm getting from Xorg.0.log: 

```
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```Now knowing that this was a problem of my own doing I took a look at my history to try and figure out what i did wrong but i'm not very savvy in such things... I'll paste some of the relevant command history

```
 55  startx
   56  su
   57  xauth
   58  ls
   59  cd ..
   60  ls
   61  pwd
   62  cd root
   63  ls
   64  pwd
   65  gedit .Xauthority
   66  su guy0203
   67  vi
   68  pwwd
   69  pwd
   70  ls
   71  cd ..
   72  pwd
   73  ls
   74  cd root
   75  man vi
   76  apropos
   77  apropos edit
   78  notepad
   79  apropos edit | less
   80  man poc
   81  man pico
   82  pico -BS .Xauthority 
   83  man xauth
   84  xauth
   85  help xauth
   86  man man
   87  man xauth
   88  man startx
   89  man x
   90  man X
   91  man 7
   92  man X
   93  man Xserver
   94  man xdm
   95  xdm help
   96  Xsecurity
   97  man Xsecurity
   98  wicd
   99  man wicd
  100  iwconfig
  101  startx help
  102  startx
  103  xauth
  104  su guy0203
  105  su guy0203
  106  startx
  107  ps
  108  man userdel 
  109  userdel guy0203
  110  history
  111  history | less
  112  adduser guy0203
  113  sudoers
  114  apropos sudoer
  115  visudo
  116  fg
  117  visudo
  118  startx
  119  ps
  120  fg
  121  startx
  122  ps
  123  fg
  124  kill -9 3829
  125  su guy0203
  126  startx
  127  su guy0203
  128  startx
  129  cp -Rf * /home/guy0203
  130  ls
  131  cd.
  132  cd ..
  133  ls
  134  cd home
  135  ls
  136  cd guy0203
  137  history
  138  man chown
  139  chown -R guy0203:guy0203
  140  chown -R guy0203:guy0203 /home/guy0203/
  141  exit
  142  nvidia xconfig
  143  nvidiaxconfig
  144  nvidia-xconfig
  145  startx
  146  nvidia-xconfig
  147  startx
  148  ps
  149  kill 6080
  150  ps
  151  man kill
  152  kill -9 6080
  153  ps
  154  startx
```I have an idea of what the problem might be but i have no idea how i would fix it. if anyone could help me it would be greatly appreciated. And if i should provide anymore information just let me know.

PS sorry if this is a bit verbose.

---

### Post by GuyZerO on 2012-02-01
I found the solution... I feel stupid because of it.

rm /etc/X11/xorg.conf

That was it. i did that hit reboot and i had a gui again...
I guess we can close this thread or what ever is done in situations like this.

---

### Post by finny388 on 2012-02-01
Good on you Guyzero
Go to thread tools above and mark this thread as solved.

It's great of you to post the solution to your issue. So many find one and don't post or even more frustratingly make one last post saying "I solved it. Thanks all, I'm good now" as if these forums aren't about sharing solutions.

Anyway, glad you got your screen back.

---

