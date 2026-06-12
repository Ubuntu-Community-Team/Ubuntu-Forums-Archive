---
title: "Xvnc using 100% cpu"
date: 2006-05-09
forum: General Help
---

### Post by eremk on 2006-05-09
Hi,
Occasionally I can't VNC on the workstation we have here at the office, and when I check the processes with the "top" command, I see that Xvnc is using up ~100% of one processor. I reboot the vnc server, and the problem is temporarily solved, but it happens again and again for some reason I don't know. The machine I'm trying to VNC on is not used for anything but running analyses (i.e. no browsing, no e-mail clients etc.), so I don't expect any memory related problems. Any ideas why this problem occurs, and how to solve it permanently? I see that this problem has been brought up couple times before, but no permanent solution so far, so I'd like to try my chances.
Thanks,
Erem

---

### Post by dereknet on 2006-05-09
I'm having the same exact problem with my 5.10 box. I will kill the process, not use VNC at all, then come back the next day with a stuck 99%+ load caused by XVNC. Any help would be greatly appreciated!

---

### Post by eremk on 2006-05-09
which vnc viewer do you use?

---

### Post by dereknet on 2006-05-10
TightVNC 1.29 from a winblows machine. I restarted yesterday when I made that post and the Xvnc process hasn't gone crazy in the mean time. So I'm assuming someone might have tried connecting via vnc when I mentioned I didn't use vnc for a day but still had the problem.

---

### Post by aebrett on 2008-07-02
I've seen a similar issue on hardy (with Xvnc 4.1.1) when port scanning with nmap, or creating a short-lived raw TCP connection with nagios2. Full version information:

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation

Attaching to the process with strace gives me the following output repeated over and over again:

select(256, [0 1 3 4 5 6 7 8 9], NULL, NULL, {78, 725000}) = 1 (in [3], left {78, 725000})
accept(3, 0, NULL)                      = -1 EINVAL (Invalid argument)
time(NULL)                              = 1214993292
write(2, " XserverDesktop: XserverDesktop:"..., 69) = 69
write(2, "              connection: Invali"..., 48) = 48
gettimeofday({1214993292, 448357}, NULL) = 0
gettimeofday({1214993292, 448460}, NULL) = 0
gettimeofday({1214993292, 448554}, NULL) = 0
gettimeofday({1214993292, 448645}, NULL) = 0

---

