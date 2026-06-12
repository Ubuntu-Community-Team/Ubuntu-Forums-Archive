---
title: "error when running xdiagnose"
date: 2012-09-15
forum: General Help
---

### Post by claracc on 2012-09-15
Using ubuntu 12.04, gnome fallback desktop.

When I run xdiagnose from menu nothing happens.

When I run xdiagnose from xterm, I obtain:

```
clara@clara1:~$ xdiagnose &
[1] 16186
clara@clara1:~$ Error: No /etc/default/grub present

```

Certainly I am using grub legacy, i.e.: 

```
clara@clara1:~$ grub --version
grub (GNU GRUB 0.97)

```

For this reason grub is not in /etc/default/.

As grub legacy is still supported (till 2017 I read), in what way I can run xdiagnose tool without obtaining this error?.

Could this problem be a bug?

Thanks in advance

---

### Post by Epodx64 on 2012-09-15
It looks like it is indeed a bug trying running xdiagnose as sudo and it shouldn't return the error. (Though you shouldn't have to run it as sudo but a bug's a bug)

ubuntu-bug 769419

---

### Post by claracc on 2012-09-16
Yes I have seen the bug in launchpad but I think this is a different one because xdiagnose doesn't take into account there is not grub in /etc/default/ because I am not using grub2 but grub legacy.

I think the script would have to take into account the possibility of using grub legacy.

---

### Post by Epodx64 on 2012-09-16
does running xdiagnose with sudo return the error?

---

### Post by claracc on 2012-09-17
When I run xdiagnose with sudo, nothing happens. Not asking for password neither.

```
clara@clara1:~$ sudo xdiagnose &
[1] 4762
clara@clara1:~$ 

```

If I run ps -ef, I can see the process running, but nothing happens.

```
clara     4704  4699  0 07:40 pts/0    00:00:00 bash
root      4762  4704  0 07:40 pts/0    00:00:00 sudo xdiagnose
root      4781     2  0 07:40 ?        00:00:00 [kworker/0:2]
clara     4821  4699  1 07:41 pts/1    00:00:00 bash
clara     4896  4821  0 07:41 pts/1    00:00:00 ps -ef

```

---

