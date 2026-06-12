---
title: "Package Operation Failed"
date: 2011-09-19
forum: General Help
---

### Post by ernestj on 2011-09-19
I keep on getting the following error when I try to download software:

"The installation or removal of the software package failed."

However, software is installed. 

Did I somehow break my Ubuntu?

Thanks,
Ernie

---

### Post by seawolf167 on 2011-09-19
Run the commands

```
sudo apt-get update
sudo dpkg --configure -a
```

and post the results in CODE tags when you reply

---

### Post by ernestj on 2011-09-19
says the following:

Error! Cannot locate /usr/src/synaptics-1.0.0.dkms.tar.gz
File does not exist
dpkg: error processing synaptics-dkms (--configure):
  subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 synaptics-dkms

---

### Post by seawolf167 on 2011-09-19
Try running the commands in the other order, else remove the package if neither of them work

```
sudo dpkg --configure -a
sudo apt-get update
```

and if they still don't work, try

```
sudo apt-get purge synaptics-dkms
```

---

### Post by ernestj on 2011-09-19
solved, thank you!!!!

---

### Post by seawolf167 on 2011-09-20
Which command(s) solved it for you?

Also, please mark this thread as solved under "Thread Tools".

---

