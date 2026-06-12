---
title: "How do I give permissions to partitions?"
date: 2010-03-06
forum: General Help
---

### Post by the lemming on 2010-03-06
Hello

I have a laptop with a 250gb drive.

It is partitioned in the following way.

Vista 80gb
Ubuntu 40gb
Data 121 gb  (Formatted as NTFS)

And I have a Windows 7 computer

I have Samba installed on Ubuntu 9.10 and I can see the Windows7 computer from my Ubuntu laptop.  However I can not see my Ubuntu partition or the Data partition over the network.

How do I give permission for the Data partition, which is NTFS and the Home partition on Ubuntu?

I DO NOT want to give permission to the "/" partition.

Cheers

---

### Post by cogier on 2010-03-06
Have you "shared" the folders? If not, from Ubuntu, right click on the folder you want to share and select properties. Click the "Share" tab and choose to share the folder. You will need to download the necessary software when offered. You will then need to reboot. The folders you share should then be visible from Windows.

---

### Post by the lemming on 2010-03-06
I seem to be having problems.

The first one is that I can not share an entire partition which for all intent and purposes is a seperate drive.

I can mount it, and look at it from Ubuntu or the windows OS on the laptop.  But when I click on the properties of the drive called Data and click the Permissions tab I get the following message

The Permissions of "Data" could not be determined.


On the plus side I have managed to share a file within the partition.  Is this the only way I can do things, otherwise I would love to share the entire partition.




My last question is how do I share all the files and folders within my Home Directory because they are not showing up on the network?
Only the one folder that I have just shared has shown up.

---

### Post by FiveSidedPoly on 2010-03-06
You can use terminal and set the whole partition or you can do it through Samba.
 
 
Terminal
 
sudo chmod -R 777 /home
 
 
 
For Samba you could place and entry like the below, but this only allows the actual user of each home folder to see it (%S)
 
[homes]
comment = User Home Shares
valid users = %S
create mode = 0770
directory mode = 0770
broweseable = no
read only = no
 
 
You could also use to make a public home folder to share then.
 
[Public Home]
comment = Public Home Shares
path = /home/Public
ceate mask = 0777
directory mask = 0777
browseable = yes
read only = no
writeable = yes
force user = nobody
force group = nogroup
 
You should be able to also use the last one but change it for your data partition by using /data instead of /home/Public. Then make sure you make a directory called "Public" in the /home directory. Then restart samba.
 
Note: these public options open it up and force the user nobody and the group nogroup. If you aren't sure about any of this I suggest reading up on it more. The last thing you want to do is open up shares and not know what you've done.
 
 
Here's some helpful info for Samba if you haven't checked it out already.
 
[HOWTO: Samba Setup]("http://http://ubuntuforums.org/showthread.php?t=202605")
 
 
Here's a cool little tool to help you figure out what chmod permissions to use.
 
[Chmod Calculator]("http://http://www.webweaver.nu/html-tips/chmod.shtml")
 
 
Hope that helps some. :)

---

