---
title: "Can't install WINE in 64 bits Ubuntu 12.04.1"
date: 2012-08-26
forum: General Help
---

### Post by vexorian on 2012-08-26
It is driving me insane.

It happens to me with the official repositories or the ubuntu-wine PPA, with any WINE version.

In terminal, sudo apt-get install wine, or sudo apt-get install wine1.5 or sudo apt-get install 1.4...: 

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

(According to synaptic, no package in my system is broken).

In synaptic:
> The following packages have unresolved dependencies (...)
wine:
 Depends: wine1.4 but it is not going to be installed

I already tried this:

```

echo "foreign-architecture i386" | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo chmod 644 /etc/dpkg/dpkg.cfg.d/multiarch
```

No help.

---

### Post by raja.genupula on 2012-08-26
```
sudo apt-get install -f
```

---

### Post by vexorian on 2012-08-26
^ I kept doing that and it was not doing anything (There really were no broken packages).

So, it seems I fixed it. I do not know if I do, but apt-get is letting me download all the required packages now when I do apt-get install wine1.5.

Here is what I did: I manually did sudo apt-get instal {package_name} for each dependency error I had. At the end I found that the root of all dependency errors was libfontconfig1:i386 which did not want to get installed. It seems that the repos had version 2.8.0-3ubuntu9.1 of libfontconfig1:amd64 but only version 2.8.0-3ubuntu9 of libfontconfig1:i386. I say it seems because when I went to this page: [http://packages.ubuntu.com/precise-updates/libfontconfig1](http://packages.ubuntu.com/precise-updates/libfontconfig1) there were debs for both of them.

Then I downloaded both debian files (amd64 and i386) of that page. (trying just i386 did not work) and installed them manually (At the same time). It set some gears into motion it seems, as now when I do apt-get install wine1.5 it does not find dependency errors before attempting to download (maybe it will find them during installation, but won't find out till my slow internet connection downloads 200MB of data)

Edit: Yeah, I can now run WINE. Happy.

---

### Post by vexorian on 2013-04-09
I had the same problem in another 64 bits computer with 12.04.2 two weeks ago. Well, not exactly the same, the conflicting package was different.

Today I was preparing to have the same problem in a third setup. But didn't.

I *think* that the way to prevent this issue is to make sure to have all packages completely updated before adding the wine ppa.

---

