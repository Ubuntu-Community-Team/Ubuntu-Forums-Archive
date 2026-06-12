---
title: "server hangs"
date: 2009-11-17
forum: General Help
---

### Post by ub007 on 2009-11-17
Hi,

my server(kernel) hangs or rather task blocked for 120 seconds messages are spewed on to the screen when I'm copying files over a NFS share.

I'm trying to figure out which process is causing the hang, 

did this-

> echo 8 > /proc/sysrq-trigger and setting up serial console logging helped collect some backtraces.

but',I need to grab more info...eg strace of certain pids, meminfo output,list of open files etc when/during the hang occurs.

any ideas/suggestions on how to go about it.

I tried this script in a loop

> dmesg | grep "blocked for....." -q
is $? == 0; then
dmesg > file
cat /proc/meminfo > /file2
...
,,,,
exit 0
fi
done


This isn't working, in the sense  no logs are being grabbed, guess the script stalls when the kernel hangs, i'm unsure

any help is appreciated

Cheers
David

---

