---
title: "remote manage multiple m/c's"
date: 2009-07-30
forum: General Help
---

### Post by jadhav333 on 2009-07-30
I wish to setup a system as follows:

I have multiple (for eg. 6) machines san's monitors or keyboard or cd/dvdrom, connected on a network.. I have another (single) machine which has all the required peripherals..

1: I want to be able to install ubuntu on all the multiple m/c's remotely via the single m/c

2: I would like to remote boot the multiple m/c's via the single m/c

3: I would like to manage the multiple m/c's via the single m/c

Is this feasible? How?

---

### Post by t4thfavor on 2009-07-30
Option 1.
Theres a netboot method for almost any OS, you will need a tftp server, and a dhcp server. Make sure that your add whatever kernel option that enables an ssh console for install. Then you can use the other machine as the SSH client. 
Option 2.

If all machines are the same, you could work out a custom boot/install script. Then boot them off the network, and they will install without your interaction. When they are done there will be a user(you configured in the script) which you can use to ssh into them and manage them. 

There are also serial console installs if that is an option for you.

Its possible, but its going to take more work than just moving the Monitor plug to each PC.

---

### Post by jadhav333 on 2009-07-30
..

---

### Post by jadhav333 on 2009-07-30
1) FOR OPTION2: where do you place the boot script - in the m/c to be booted or in the other networked m/c? Where can I find more info on creating such scripts?

2) FOR OPTION2: How do you initiate a network boot? Pls bear with me if the question appears noob.

3) Do we have any application that we can run on the single m/c to access the screen of the other (multiple) m/c's.. somewhat like remote desktop access..

---

