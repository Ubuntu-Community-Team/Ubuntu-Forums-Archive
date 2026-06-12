---
title: "start-stop-daemon missing in 11.10"
date: 2012-02-02
forum: General Help
---

### Post by DVCnerfherder on 2012-02-02
I had some power/battery issues with my Dell Latitude D430 running Ubuntu 11.10 and it crashed the other day.  On reboot it prompted me to run in recovery mode, which I did.

Now, when I attempt to run the update manager no packages will install and I get an error message which reads in part:

"warning: 'start-stop-daemon' not found in PATH or not executable."

When I check the contents of /sbin, start-stop-daemon does not appear to be present.  How can I access the appropriate package to reinstall it and whatever else might be missing from /sbin.  Thanks.

---

### Post by lechien73 on 2012-02-02
Hi and welcome to the forums,

If you're sure that start-stop-daemon is in fact missing from /sbin, then you can recover it as follows:

1. Download the dpkg package from [http://packages.ubuntu.com/oneiric/dpkg](http://packages.ubuntu.com/oneiric/dpkg)

2. Copy the file into a temporary location:

```
mkdir ~/dpgk_temp
cp ~/Downloads/dpgk*.deb ~/dpkg_temp
cd ~/dpgk_temp
```

3. Extract the files from the archive:

```
ar x dpkg*.deb
tar xfvz data.tar.gz
```

4. Copy the file to /sbin:

```
sudo cp ./sbin/start-stop-daemon /sbin
```

5. Try update the apt information:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by DVCnerfherder on 2012-02-02
That did it!  Thanks for the assist.  My system is now up-to-date (or so it tells me...)  ;)

---

### Post by lechien73 on 2012-02-02
Great stuff, I'm glad it helped :)

If you get chance, please could you use the **Thread Tools** menu at the top and mark the issue as [SOLVED]?

Thanks

---

