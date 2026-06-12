---
title: "Instance self-terminates, does NOT release resources"
date: 2009-11-19
forum: General Help
---

### Post by ewgates on 2009-11-19
_[SIZE=3][FONT=Calibri]Setup: [/FONT][/SIZE]_
 
[SIZE=3][FONT=Calibri]Two Dell E6400 laptops, one setup as the front end with Cloud and Cluster Controller, the other setup as the Node. [/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Ubuntu 9.10 64 bit server with cloud has been installed. [/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]The image is the “Ubuntu 9.10 RC – Karmic Koala (32bit) Image Version 20091022” installed from the eucalyptus login, “store” menu. I never did get the 64 bit version to run in an instance (described in a previous ubuntu forum log).[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]The only user is admin. [/FONT][/SIZE]
 
_[SIZE=3][FONT=Calibri]Problem Description:[/FONT][/SIZE]_
 
[FONT=Calibri][SIZE=3]Ran an instance as admin, using the command “euca-run-instances emi-E114108C –k mykey –t m1.large” and let run for a few hours while investigating how to install java. [/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]SSHd into the instancewith the command “ssh –i ~/.euca/mykey.priv ubuntu@192.168.2.100”.[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]On the instance, modified /etc/apt/sources.list to include repositories for java installation. [/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]Updated with the command “sudo apt-get update”.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Installed Java with the command “sudo apt-get install sun-java6-jdk”.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The command “java –version” shows “java version 1.6.0_15”[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Exited instance, went home.[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]Next morning (hours later) instance does not exist. [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]“Euca-describe-images” shows the same images as the previous day, no change.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]“Euca-describe-instances” shows nothing, no instance running.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]“Euca-describe-availability-zones verbose” shows no available VMs.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]“euca-describe-keypairs” shows the expected key.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]“euca-run-instances emi-E114108C –k mykey –t m1.large” provides the error “Not enough resources: vm instances”[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The cc.log on the Front End shows no obvious errors and thinks that i-4F370846 is still cached and is being refreshed.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The nc.log on the Node shows no obvious errors and shows that the image i-4F370846 is still running.[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]The node command line did show the error “[515854.823959] killed process 1735 (apache2)”.[/SIZE][/FONT]
 
[SIZE=3][FONT=Calibri]_Summary:_ There are two issues.[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]1. The instance self-terminated overnight.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]2. The cloud status commands show that no instances are running but there are no VM resources available to run.[/SIZE][/FONT]
 
_[SIZE=3][FONT=Calibri]Questions:[/FONT][/SIZE]_
 
[FONT=Calibri][SIZE=3]What are the possible reasons for a self-terminating instance, especially one that has been running for hours?[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]How can I recover resources so that I can run another instance, ssh into it, then run java programs for experiments?[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Why did I have to modify sources.list in order to install java, especially when there is no explanation in the documentation?[/SIZE][/FONT]

---

### Post by ewgates on 2009-11-23
[SIZE=2]I reinstalled both the Front End and the Node (both Dell E6400 laptops) with the 32 bit version of the Ubuntu 9.10 with cloud (instead of the 64 bit) and ran an instance with the “Ubuntu 9.10 RC – Karmic Koala (32bit) Image Version 20091022”.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]After the weekend, a "euca-describe-instances" shows that the instance is still running.[/SIZE]

---

