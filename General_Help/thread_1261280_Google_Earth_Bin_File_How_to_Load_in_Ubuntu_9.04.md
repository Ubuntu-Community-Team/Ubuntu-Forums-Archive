---
title: "Google Earth Bin File How to Load in Ubuntu 9.04"
date: 2009-09-08
forum: General Help
---

### Post by robbiechad on 2009-09-08
Hi, I,m running Ubuntu 9.04 with everything seeming to work OK, I,m not too well up on terminal commands, I have just downloaded Google Earth for Linux and it is a bin file loaded onto my desktop how do I turn it into an RPM to enable the package manager to load it into my system? Many thanks in advance.

---

### Post by oldos2er on 2009-09-08
RPM packages are for Red Hat and its derivative distros. Ubuntu is based on Debian, so it uses deb packages.

   But you've got the *bin file, no converting is necessary. Run these commands one at a time in a terminal:
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

 This will install GE to /opt.

---

### Post by P4man on 2009-09-08
Before giving you the actual answer to your question, let me suggest an alternative and "better" approach. Add the medibuntu repository to your software sources. After doing that, you can install non open source applications like Skype, Google Earth, etc just like you install anything else: Applications > Add/remove > select, install, done.

To enable medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Advantage of this, is that its later easier to uninstall, the packages ("programs") are tested, and any updates to them arrive along with all other ubuntu updates.

Now, if you must use the google installer, then right click the file you just downloaded, properties, permissions and enable the "allow executing".
Then open a terminal, change to the folder where you put the file (eg "cd Desktop") and run "./GoogleEarthInstallerOrwhateverItsname.bin"

---

### Post by robbiechad on 2009-09-08
P4Man , many thanks for that I did it the way you said and have now got Google Earth on my system, I do not know if its playing right, but will have to have a play about with it. Thanks a lot.

---

