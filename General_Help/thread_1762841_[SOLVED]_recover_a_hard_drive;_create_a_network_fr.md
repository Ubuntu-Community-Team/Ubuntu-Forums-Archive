---
title: "[SOLVED] recover a hard drive; create a network from two ubuntu natty"
date: 2011-05-19
forum: General Help
---

### Post by cementtruck on 2011-05-19
This isn't a question, but a story of triumph:

Yesterday I made  girlfriend's laptop unable to boot after deleting some windows files by  accident.  So this is the story of how I fixed it.  (I'm relatively new  to ubuntu, and this might not have been that difficult.)

General outline:
1.  How to boot the broken computer
2.  How to backup the files from her computer 
     a.  How to physically create a two computer network 
     b.  How to setup a two computer network with both computers using ubuntu
     c.  How to share files across a two computer network
3.  Re-install windows (not talking about this here)

Definitions  (i learned what these were while doing this project in case you want to  preview them before hand on wikipedia / google)
BIOS
NTFS
Ethernet cords vs. cross over cable
static IP
ping (network connection test)
SSH 
fstab (a disk mounting configuration file)

1.  How to boot the computer
     a.  Download the ubuntu operating system to a thumb drive / cd on a working computer
          [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
     b.  Plug the operating system in to the broken computer (USB for thumb drive / CD drive for CD)
      c.  As the broken computer is attempting to start, hit the key to enter  the BIOS section of the computer.  (The key should appear at startup if  you watch closely)
     d.  Change the settings to boot from an external drive (i.e. the USB or CD) to install the ubuntu operating system.
      e.  After installation of ubuntu, you should be able to see the hard  drives on your computer (like C: ect.), including the windows drives.   These windows drives (in most cases) have a different formatting than  the ubuntu Linux called NTFS.  You may need to do some extra work if  they don't show up automatically. 
     f.  You should be able to see the files on the broken computer at this point using ubuntu

2.  How to backup the files / Part A:  How to physically create a two computer network
     a.  Both the broken computer and my laptop had ethernet jacks, so this is how I shared the data.
      b.  Ethernet cords are not capable of sharing information directly in  most cases.  (I read Windows 7 may be capable of this, but I did not use  this option myself.)  See the distinction between ethernet cord vs.  crossover cable.  
     c.  I made my ethernet cord into a crossover  cable by splicing the wires (google: "convert ethernet to crossover  cable").  You really only have to make these changes:  orange->green,  green->orange,  stripped orange->stripped green,  stripped-green->stripped-orange.  (If you know how to soder consider  joining the wires that way; if you have the money buy a crossover  cable.) 
     d.  You can plug the "crossover cable" (modified  ethernet cord) into the jacks on the broken computer and the computer  you will use to store the transferred files.

2.  How to backup the files / Part B:  How to setup a two computer network in ubuntu
      a.  Setup the network for the ethernet connection by finding the  "Network Connections" icon  (Power [top-right corner of desktop] ->  "system settings" ->  "internet and network")
     b.  Network  Connections:  Wired tab -> "auto eth0" (click to highlight; should  appear automatically) -> "Add" -> "IPV4 Settings" (its a tab)  -> Method:  "Manual" (need to change to this) -> Add (on right)  -> change "Address" to "192.168.0.1" -> click "Save..."
     c.  For the other computer, repeat (a.) and (b.), except set the "Address" to "192.168.0.2"
     d.  Run these terminal commands for the first computer:
/sbin/ifconfig eth0 192.168.0.1 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.2 eth0"

and for the second:

/sbin/ifconfig eth0 192.168.0.2 netmask 255.255.255.0 up
/sbin/route add -host 192.168.0.1 eth0

     e.  Test the system  (expect this not to work the first time)
Computer 1:
ping 192.168.0.2

Computer 2:
ping 192.168.0.1

You should recognize a correct output as containing: "0% packet loss" "ms"
If you reached this point, your computers are talking to each other.  Congrats!

2.  How to backup the files / Part C:  How to share files across a two computer network
a.  Use the SSH program downloaded with the terminal command:
 sudo apt-get install openssh-server openssh-client
(I did this for both computers.)
b.  Setup the program:
Computer 1 terminal command:
sudo /sbin/route add -host 192.168.0.2 eth0

Computer 2 terminal command:
sudo /sbin/route add -host 192.168.0.1 eth0

c.  Setup the keys: 
[http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html](http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html)

d.  Connect to the other computer
From computer two to computer one type in the terminal 
sftp user_name@192.168.0.1

e.  You should see a ">" indicating your in sftp.  google "sftp commands" for more information

f.  If you cannot find the mounted drive in sftp, it may be "mounted" in a folder in the ubuntu folder tree
Terminal command:
nano /etc/fstab

This  "fstab" file contains the information used to mount drives so you may  want to learn more about how it works.  (Or, you may want to just look  in the folder pointed to by the second word of any row.)


Links I found useful:
                        [http://ubuntuforums.org/archive/index.php/t-1126718.html](http://ubuntuforums.org/archive/index.php/t-1126718.html)
 

 [http://vikashazrati.wordpress.com/2008/02/03/quicktip-transferring-files-between-two-ubuntu-systems/](http://vikashazrati.wordpress.com/2008/02/03/quicktip-transferring-files-between-two-ubuntu-systems/)
 

 
3.  After transferring the important files you are free to wipe the  hard drive and install your operating system.  (Use step 2 to transfer  the files back.)

OK... so hope that helps someone else.  Sure  took me AWHILE to figure that stuff out.  I just tried to get it working  for if you want to share any theory about why it worked please feel  free.

Cheers--:smile:

---

