---
title: "segmentation fault in flash"
date: 2009-10-31
forum: General Help
---

### Post by viralmeme on 2009-10-31
Ubuntu 9.04 on a 3GB USB device
Flash Player 10 ..
--

$ strace -f -eopen firefox &> /tmp/ffox.log.txt &
$ renice -11 firefox.pid

.. eventually crashes on opening/closing lots of flash vids ..

$ tail ffox.log.txt

[pid  6157] open("/home/ubuntu/.macromedia/Flash_Player/#SharedObjects", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 72
[pid  6157] open("/home/ubuntu/.macromedia/Flash_Player/#SharedObjects/DNRNKXS3/s.ytimg.com/soundData.sol", O_RDONLY|O_LARGEFILE) = 72
[pid  6157] --- SIGSEGV (Segmentation fault) @ 0 (0) ---
[pid  6157] --- SIGSEGV (Segmentation fault) @ 0 (0) ---
upeek: ptrace(PTRACE_PEEKUSER,6259,44,0): No such process
Process 6259 detached
[pid  6270] +++ killed by SIGSEGV +++
[pid  6266] +++ killed by SIGSEGV +++
[pid  6263] +++ killed by SIGSEGV +++
[pid  6262] +++ killed by SIGSEGV +++
[pid  6168] +++ killed by SIGSEGV +++
[pid  6167] +++ killed by SIGSEGV +++
[pid  6166] +++ killed by SIGSEGV +++
[pid  6160] +++ killed by SIGSEGV +++
[pid  6159] +++ killed by SIGSEGV +++
[pid  6260] +++ killed by SIGSEGV +++

---

