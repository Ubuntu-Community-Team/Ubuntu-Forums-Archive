---
title: "Synaptic has a no entry sign and won't launch"
date: 2009-07-17
forum: General Help
---

### Post by mike hunt on 2009-07-17
This is what Synaptic says when I try to launch it.

E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'

There isn't a status folder/file in the dkpg directory.

Can anyone help with this please?:)

---

### Post by munky99999 on 2009-07-17
what were you doing before this started to happen? If it's a completely fresh install. You might just want to do another install.

---

### Post by michy99 on 2009-07-17
What error messages do you get if you run this in the terminal?```
sudo apt-get update
```

---

### Post by mike hunt on 2009-07-17
> **michy99 said:**
> What error messages do you get if you run this in the terminal?```
sudo apt-get update
```

 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B] Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB] Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                  Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                       Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources   Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [56.3kB] Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2097B] Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [16.7kB] Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [611B] Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [19.4kB] Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [5238B] Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B] Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B] Fetched 150kB in 0s (225kB/s)                       Reading package lists... Error! E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory) E: The package lists or status file could not be parsed or opened.  Seems to be the bloody status thing again

---

### Post by ronaldprettyman on 2009-07-17
> **mike hunt said:**
> Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B] Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB] Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                  Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                       Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources   Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [56.3kB] Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2097B] Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [16.7kB] Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [611B] Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [19.4kB] Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [5238B] Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B] Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B] Fetched 150kB in 0s (225kB/s)                       Reading package lists... Error! E: Could not open file /var/lib/dpkg/status - open (2 No such file or directory) E: The package lists or status file could not be parsed or opened.  Seems to be the bloody status thing again

ps -A|grep apt
ps -A|grep dpk
ps -A|grep -i synaptic
Your probably running one of these. You can't run synaptic and apt at the same time. Its a conflict of interest. I mean a potential error and apt believes your trying to install software with two different applications. Its trying to avoid potential failure.

---

### Post by michy99 on 2009-07-17
What do you get from this?```
ls -la /var/lib/dpkg
```

---

### Post by CatKiller on 2009-07-17
> **mike hunt said:**
> 'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'

There isn't a status folder/file in the dkpg directory.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by mike hunt on 2009-07-17
> **CatKiller said:**
> ```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Synaptic launches again now after doing that :)
Thanks :D

Now i've got this error lol.....E: Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle.

I also got the error when trying to install libc6 to see if that would sort the problem.

---

