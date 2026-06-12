---
title: "Error message with apt-get"
date: 2011-04-21
forum: General Help
---

### Post by whittaker on 2011-04-21
Hello, 

I am unable to update apt-get and i am unable to install any software.

The following message when i use the sudo apt-get update command

> 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release: The  following signatures couldn't be verified because the public key is not  available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

When i for example try to install the gcc i also get weird feedback

> 
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I though it was that they where already installed on the comp, however, the computer keeps telling me that gcc is not installed. I am not quite sure what to do

I am using the latest version of ubuntu (10.10)

If someone can help me find the solution to this problem i would be grateful!!

---

### Post by stealth. on 2011-04-21
> **whittaker said:**
> Hello, 

I am unable to update apt-get and i am unable to install any software.

The following message when i use the sudo apt-get update command


When i for example try to install the gcc i also get weird feedback

I though it was that they where already installed on the comp, however, the computer keeps telling me that gcc is not installed. I am not quite sure what to do

I am using the latest version of ubuntu (10.10)

If someone can help me find the solution to this problem i would be grateful!!

Read [http://ubuntuforums.org/showthread.php?p=1653773](http://ubuntuforums.org/showthread.php?p=1653773)

---

### Post by dino99 on 2011-04-21
medibuntu server is often busy or down, dont worry much about it. You can open synaptic (system admin synaptic) repo tab to uncheck medibuntu and the lines checking for sources if any.

note that bugs are often between chair and keyboard :(  (you might first understand what you request)

---

