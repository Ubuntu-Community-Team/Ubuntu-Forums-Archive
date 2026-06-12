---
title: "cleanup /tmp at boot time"
date: 2010-05-07
forum: General Help
---

### Post by tall-male on 2010-05-07
The automatic cleanup of /tmp at boot time is not working. It wasn't working in Ubuntu 9.10, neither in the new 10.04.

The problem seems to happen using a separate /usr partition.

According to /etc/init/**mounted-tmp.conf**, cleaning starts when /tmp is mounted:
[INDENT]start on mounted MOUNTPOINT=/tmp[/INDENT]

However, the script needs /usr/bin/find to cleanup /tmp. Cleanup is failing since /usr is not there (is not mounted) when cleaning starts. Therefor, /tmp is never cleaned


Changing it to:
[INDENT]start on local-filesystems[/INDENT]

solved the problem. The cleanup is only started when all local file systems are mounted.

Now, imho this should be changed in the code....

---

### Post by frederickjh on 2010-07-07
Hi tall-male!

I have confirmed what you are saying is true, however this is not the place to file bug reports. It is good to inform the users here. However it would be good if you would go to bugs.launchpad.net and report this so it can be fixed by the developers.

---

### Post by dcstar on 2010-07-07
> **frederickjh said:**
> Hi tall-male!

I have confirmed what you are saying is true, however this is not the place to file bug reports. It is good to inform the users here. However it would be good if you would go to bugs.launchpad.net and report this so it can be fixed by the developers.

Yep, fairly pointless posting these things without filing a bug report.

All people have to do to become a real part of the Linux community is do the right thing and post bug reports, then people in the future benefit from less problems as all of us currently do because of the efforts of those in previous times.

---

### Post by frederickjh on 2010-07-07
Ok, I did not sure if anyone else will. Here is the bug report FYI

[https://bugs.launchpad.net/upstart/+bug/602659](https://bugs.launchpad.net/upstart/+bug/602659)

---

### Post by nemilar on 2010-07-07
Thanks for filing the bug report....

One thing that makes Linux great compared to Windows, is that in Windows whenever something crashes everyone always clicks "Do not report" on that darn error report box.  But Linux users tend to be more active, and more willing to file bug reports to get things fixed.

My hunch is because the system is more transparent; whereas in Windows, you don't even know what is going to happen if you actually *do* file a bug report, in Linux you can watch it from start to finish.

---

