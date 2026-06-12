---
title: "Synaptic Package Manager - can not update"
date: 2011-07-09
forum: General Help
---

### Post by auscanstom on 2011-07-09
Hi,

I am trying to update my Synaptic Package Manager but I get the following errors. Can any one help? The errors are:

Failed to fetch [http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/bjfs/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by raja.genupula on 2011-07-09
what is the Ubuntu version you are using ?

---

### Post by auscanstom on 2011-07-09
I'm using Ubuntu 11.04

---

### Post by raja.genupula on 2011-07-09
ok try this ```
 sudo rm -rf /var/lib/apt/lists/*
```
do "sudo apt-get update" again

---

### Post by auscanstom on 2011-07-09
Hi raja,

I have just done what you have advised and it all looks fine.

In Synaptic Package Manager when I do CTRL+R, it goes through a process of downloading package information. When I click on "show for individual files", under the status tab, I can see a lot of failed and a few done. Any idea what this is? If it shows failed, should I be concerned?

---

### Post by raja.genupula on 2011-07-09
hi auscanstom 
                     its trying to connect that server and i think due to hash index crash  things can happen like that....
   


                     
sudo apt-get update -o Acquire::http::No-Cache=True  

  please mark thread from thread tools if it is solved

---

### Post by auscanstom on 2011-07-09
thanks a lot for the help.

---

### Post by raja.genupula on 2011-07-09
:guitar: you are welcome

---

