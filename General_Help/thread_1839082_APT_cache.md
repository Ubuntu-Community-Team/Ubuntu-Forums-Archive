---
title: "APT cache"
date: 2011-09-04
forum: General Help
---

### Post by markomk on 2011-09-04
Hi! I try to open System>Administration>Synaptic Package Manager and I got this error.

"E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing liblablgtkmathview-ocaml-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.offensive-security.com_dists_pwnsauce_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."


So, how can I increase cache Limit?

Tnx :)

---

### Post by pschalkx on 2011-09-09
Hi all,

I have the same issue as markomk. So I'm stuck without being able to install or remove packages.

I tried some of the threads telling to use sudo to change a value in
- /etc/apt/apt.conf.d/20archive
or in
- /etc/apt/apt.conf.d/70debconf

but they didn't work.

Any ideas or suggestions?


"E:Dynamic MMap ran out of room. Please increase the size of APT::Cache-limit. Current value; 25165824.....
E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be opened or parsed"

---

### Post by gmargo on 2011-09-09
This is sometimes a problem on 32-bit systems.

Put the following in **/etc/apt/apt.conf** (or some file under /etc/apt/apt.conf.d/):
```

APT::Cache-Limit "40000000";

```

---

### Post by pschalkx on 2011-09-10
Hi Gmargo,

Thanks!

That did the trick :D

---

### Post by Paul Lynch on 2011-10-08
Hi,
struggling a little here. I have a problem with my APT cache limit:
[I]
Eynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf), E:Error occurred while processing aptitude (NewFileVer1), Eroblem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'[/I]

I have followed the instructions above and in other threads so I have a file in */etc/apt/apt.conf.d *called *70debconf.* with the text *APT::Cache-Limit "50331648"; *

I have changed this limit to 100000000 and 50000000 and the same error comes up stating that the cache limit is still 25165824, so I dont appear to have modified the size limit.

Any help appreciated.....

---

### Post by Paul Lynch on 2011-10-09
Bump

---

### Post by Paul Lynch on 2011-10-09
Thanks for the reply but you haven't really got any usefull contribution to a solution. Anyone out there got a suggestion ?:(

---

### Post by matt_symes on 2011-10-09
Hi

Open a terminal and type

```
sudo nano /etc/apt/apt.conf
```Enter your password. It will not be ecohed to the screen. Type in this line (or whatever value you want).
```

APT::Cache-Limit "40000000";
```Press ctrl + o to save and ctrl + x to exit.

To check it's been picked up type
```

apt-config dump | grep APT::Cache-Limit
```and check output.

Then retry. Hopefully that will fix it.

Kind regards

---

### Post by Paul Lynch on 2011-10-09
That worked a treat, thanks..... :D

---

### Post by praecipula on 2011-11-02
Still not working for me. I wonder if there's been a breaking change?
Here's what I've got going on:
I'm running Oneiric 64 Server:
```
`uname -a`
Linux [hostname ommitted] 3.0.0-12-server #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

I tried to adjust the APT::Cache-Limit in both /etc/apt/apt.conf.d/75cachelimit and /etc/apt/apt.conf.

Here's the strangeness: either file claims to have updated the cache limit:

```
`apt-config dump | grep Cache-Limit`
APT::Cache-Limit "104857600";
```

So far so good, right? Then when I update:

```
`sudo apt-get update`
...
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
Reading package lists... Error!
```

So it's as if my changes were picked up, but had no effect when running for real. Can anybody else verify, or am I just the lucky owner of a Heisenbug?

---

### Post by praecipula on 2011-11-02
Some more information:

Specifying the configuration on the command line with the -o switch results in a similar set of circumstances:

```
`apt-config -o APT::Cache-Limit="100000000" dump | grep Cache-Limit`
APT::Cache-Limit "100000000";
CommandLine::AsString "apt-config -o APT::Cache-Limit=100000000 dump";
```

```
`sudo apt-get update -o APT::Cache-Limit=100000000`
...
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
Reading package lists... Error!
```

I would assume that the command line has precedence over all configuration files, so it doesn't seem like funky or ill-prepared config would be the issue. It is almost as if apt-get is not actually using this configuration parameter.

---

### Post by gmargo on 2011-11-02
I'm surprised you even need to specify that on a 64 bit system.

Is there a chance that you are out of memory and swap space?

---

### Post by matt_symes on 2011-11-02
Hi

@praecipula

> I'm surprised you even need to specify that on a 64 bit system.

Is there a chance that you are out of memory and swap space?

This is a very good point above.

Anyway, open a terminal and type

```
grep -r APT::Cache-Limit /etc/apt 2> /dev/null
```

Post the results back here.

Kind regards

---

### Post by praecipula on 2011-11-02
Got it. Thanks everyone for the prompt responses.

Of course it was something else entirely leaking out to kick apt's butt.

Long story short, there was a provisioning script that was trying to be "efficient" by maintaining a shared copy of the apt cache directory (/var/cache/apt) between machines. In theory this would seem to be OK - in practice, it caused the permissions to be all wrong. Not only that, but I believe the shared directory would screw me eventually until I found it, since there is stuff in there - like lock files - that are not meant to be shared between machines.

So what was happening is that the MMapped file was fine, but when it would try to write to disk, it would barf. I would consider this to be a very unusual case, but I'm glad I found it.

Thanks again :guitar:

---

