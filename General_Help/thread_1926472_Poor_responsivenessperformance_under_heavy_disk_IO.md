---
title: "Poor responsiveness/performance under heavy disk IO"
date: 2012-02-16
forum: General Help
---

### Post by rowan_m on 2012-02-16
I have a large (over 10,000) number of files in my Ubuntu One directory. Each time Ubuntu One starts, `ubuntuone-syncd` goes through about a minute's worth of solid disk IO. This is irritating, as it slows desktop responsiveness to a crawl and launching other applications takes much longer than usual.

The same situation occurs if I do anything that's heavy on disk usage, it's just the Ubuntu One situation is easy to reproduce as it happens every time I log in. 

I've mitigated this a bit by running `nice` and `ionice` on `ubuntuone-syncd` and switching the IO scheduler to deadline, but it's still a noticeable issue.

Any solutions or ideas on what might improve this?

In case anyone wonders, these are the two things I've used:

`~/bin/nice.ubuntuone`
```

PID=`pgrep ubuntuone-syncd`
renice -n 19 $PID
ionice -c 3 -p $PID

```

`/etc/default/grub`
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs elevator=deadline"

```

---

