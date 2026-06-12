---
title: "adobe reader"
date: 2009-07-14
forum: General Help
---

### Post by thundaraptor on 2009-07-14
/home/xxxx/downloads/AdbeRdr9.1.2-1_i486linux_enu.bin

how do I install this bin?

---

### Post by michy99 on 2009-07-14
It would be easier to install from the repositories. Either go to System->Administration->Synaptic Package Manager and search for acroread and install, or install from terminal:```
sudo apt-get install acroread
```

---

### Post by donkyhotay on 2009-07-14
> **michy99 said:**
> It would be easier to install from the repositories. Either go to System->Administration->Synaptic Package Manager and search for acroread and install, or install from terminal:```
sudo apt-get install acroread
```

Agreed, always check the repos first. Unlike windows & osX downloading a file from a website and installing that way should be your *last* resort.

---

### Post by thundaraptor on 2009-07-14
I tried synaptic but couldn't find it.  I also got error message from terminal,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

---

### Post by michy99 on 2009-07-14
Make sure you have the partner repositories enabled in System->Administration->Software Sources.

---

### Post by thundaraptor on 2009-07-14
enabled them but system still couldn't find the file

---

### Post by michy99 on 2009-07-14
Try an update and see if it finds it.```
sudo apt-get update
sudo apt-get install acroread
```If it still doesn't find it, and you want to install the .bin file, then change to the directory where the file is and make it executable and run it.```
cd ~/downloads
chmod +x AdbeRdr9.1.2-1_i486linux_enu.bin
./AdbeRdr9.1.2-1_i486linux_enu.bin
```

---

### Post by thundaraptor on 2009-07-14
> **michy99 said:**
> Try an update and see if it finds it.```
sudo apt-get update
sudo apt-get install acroread
```If it still doesn't find it, and you want to install the .bin file, then change to the directory where the file is and make it executable and run it.```
cd ~/downloads
chmod +x AdbeRdr9.1.2-1_i486linux_enu.bin
./AdbeRdr9.1.2-1_i486linux_enu.bin
```

Update worked, what did that do?

---

### Post by mthalis on 2009-07-14
Some essential software..
[http://goblog.vergilhost.info/?p=57](http://goblog.vergilhost.info/?p=57)

---

### Post by XCan on 2009-07-15
> **thundaraptor said:**
> Update worked, what did that do?

It simply retrives an updated list of available packages, i.e., if you just added a source and did not update (it usually does that automatically if added from the GUI), your system would not be able to tell that you have new packages available.

---

### Post by scouser73 on 2009-07-15
> **thundaraptor said:**
> /home/xxxx/downloads/AdbeRdr9.1.2-1_i486linux_enu.bin

how do I install this bin?

You don't need the .bin file, there is a much easier option.

Visit here; [http://get.adobe.com/uk/reader/otherversions/]("http://get.adobe.com/uk/reader/otherversions/")

In the drop-down menu of **Select An Operating System**, scroll down to **Linux -x86 (.deb)**, click **Continue** & then click **Download Now**.

---

