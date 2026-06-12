---
title: "Empathy uninstall error"
date: 2010-08-27
forum: General Help
---

### Post by victor9098 on 2010-08-27
Hi All,

Have been trying to uninstall empathy but the following happens:

In synaptic it is shown as being installed so I try to uninstall empathy, empathy-common. Then I get the following error:

> E: empathy: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.
E: empathy-common: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

So I attempt to reinstall the programmes, again via synaptic, and the following is the result:

> E: /var/cache/apt/archives/empathy-common_2.30.2-0ubuntu1_all.deb: subprocess new post-removal script returned error exit status 1
E: /var/cache/apt/archives/empathy_2.30.2-0ubuntu1_i386.deb: subprocess new post-removal script returned error exit status 1

With that failing I did some googling and found a suggestion to try:

> dpkg --remove --force-remove-reinstreq [package name]

I gave this a try but still got errors:

> dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 200638 files and directories currently installed.)
Removing empathy ...
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 156, in <module>
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 116, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or directory: '/usr/share/gconf/defaults/20_une-gconf-default'
dpkg: error processing empathy (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 empathy

If anybody could suggest what I could try now or is there something I am doing wrong I would really appreciate the help!

Thanks

---

### Post by quixote on 2010-08-30
I see a bug report about this with a [suggested workaround]("https://answers.launchpad.net/ubuntu/+question/114259"):```
sudo touch /usr/share/gconf/defaults/20_une-gconf-default  *[this creates the file it complains about not finding]*
```

Then run this command:

```
sudo aptitude purge empathy
```

Then run the following commands:

```
LANG=C;sudo aptitude install -f   *[I have no idea what the LANG=C; part does...]*
LANG=C;sudo aptitude update
LANG=C;sudo aptitude dist-upgrade
```

It didn't solve the problem in that case, and it may not in yours, but let's hope for the best :D.

---

### Post by victor9098 on 2010-08-30
Thanks for the reply and the effort you went to but I finally gave up as it seemed to be affecting the installation of other software and updates. So I just did a fresh reinstall and started from scratch.

Everything is back to normal now but this was a major inconvenience.

Thanks again

---

### Post by quixote on 2010-08-30
Sometimes reinstalling is really the best solution.  I don't know why they keep pushing empathy at us. (The program, not the real thing :D) For me, it's not a patch on Thunderbird, and it can be a real pain to get rid of.  Still, good that the problem is behind you.

---

