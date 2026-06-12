---
title: "error in terminal command"
date: 2012-02-07
forum: General Help
---

### Post by smidhunraj on 2012-02-07
I removed firefox using synaptic pacakage manager when i encountered many error  related to mozilla...
Then  when i tried to reinstall using
sudo apt-get install firefox

close failed in file object destructor:
Error in sys.excepthook:

Original exception was:
/var/lib/dpkg/tmp.ci/preinst: 74: awk: not found
close failed in file object destructor:
Error in sys.excepthook:

---

### Post by dino99 on 2012-02-07
into a terminal, run:

sudo rm  /var/lib/dpkg/tmp.ci/preinst
sudo apt-get update

---

