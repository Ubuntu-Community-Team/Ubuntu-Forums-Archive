---
title: "connecting two computers with a crossover cable"
date: 2006-03-21
forum: General Help
---

### Post by jofre on 2006-03-21
Hi everbody,

I am trying to connect two computers. I don't have a burner in my old laptop but I would like to backup some staff. For that, I thought that the easiest way would be to get a crossover cable and transfer the files to my desktop where I do have a burner.

I right click, very windows like ;) , and click in share folder, which installed NFS. I did this in both machines. Then I plug the crossover cable and try to go to Places-->NetworkPlaces, but there was nothing there.

I google a little bit. After reading a bit I understood that I have to change the network configuration to be static IP, and just put:
desktop 169.169.69.69 (I had to chose a ease number :)  )
laptop 169.169.69.68

I use the ping utility in Applications-->SystemTools-->NetwoorkTools (I am not an expert obiously)
The output was positive, the two computers were connected!

but, how can I transfer the files from one computer to another?


Thanks in advance, Jofre.

---

### Post by tomski on 2006-03-21
i would change the IP address of each machine as you have selected public IP's so if one of the machines in question is also connected to the internet it will want to go out of that route so use the following:
PC A = 192.168.1.1  subnet = 255.255.255.0
PC B = 192.168.1.2  subnet = 255.255.255.0

if you have no joy try installing webmin with the correct modules on both PC's then it should simplify the whole process ie:

goto  applications -->accesories -->terminal (a window will appear similar to command prompt for windows)
type the following:

sudo apt-get install webmin webmin-export webmin-samba

when all is installed open a web browser and type:

[https://localhost:10000](https://localhost:10000)

login to it using:

username: root
password: use the system password for sudo!

if it will not let you in try to create the root account by typing:

sudo passwd root
you will be asked for the sudo password followed by a NEW UNIX password use the same password you typed in for the sudo and will now have a root account on that PC and try to login again to webmin

when you are in webmin if you go to the server section you should see the NFS export section go there and make the changes you need do this for both PC's 
also if this is all correct you can have webmin avaliable for access by each PC so you dont have to keep changing keyboards but you will have to change one of the file that webmin uses to configure basic settings (/etc/webmin/miniserv.conf/)

hope this helps and remeber that having a live root account can be dangerous if used in the wrong hands????

---

### Post by ZylGadis on 2006-03-21
There is a much simpler way to do that, actually. You don't need webmin for something as simple as copying files.

1. Your ip's are ok as long as your machines are not connected to the internet. You know they ping each other, so you don't need to change them.
2. Open synaptic on one machine, and install openssh (don't remember the exact name of the package, the full name is something like Open SSH Server). That would give your other machine the means to connect to the one where you put openssh.
3. Open Ubuntu Places (a menu between Applications and System on your menubar). Choose Connect to Server... Choose SSH from the dropdown list, and put in the ip of the machine where you just installed openssh. Click OK (you may fill the other fields too but it's not necessary), and you should have a new icon on the desktop for connecting to that server. Click on the icon, type in whatever it asks of you (username and password are your other computer's username and password - remember you are connecting there), and browse freely, copy files, etc.

Hmm, I just saw that in order to install openssh you need internet :) So reverse steps 1 and 2.

Again, do not use webmin. You may get in serious trouble if you don't know what you are doing. Besides, ubuntu has no root for a good reason, and enabling it breaks that reason. I've no idea what the guy in the above post thought, giving such instructions to a newbie.

---

### Post by MJSOnline on 2006-03-21
[QUOTE=Alex.P]Again, do not use webmin...[/QUOTE] Good point as it very powerful in the hands of a newbie... M

---

### Post by jofre on 2006-03-21
Thanks lads. 
Zylgladis system work perfectly!!!

The first post look very confusing, i am not an expert in linux but i have been playing around enough to know that it could not be that tricky!

I was surprised that nobody mentioned telnet. I used in windows ages ago, I just did not remember a single command of it. I use google but the information was very vague, nothing concrete. (step1, step2...)

Anyway, thanks a million.
Jofre.

---

### Post by ZylGadis on 2006-03-21
You are welcome :) 
Regarding telnet: telnet is inherently insecure, as it sends everything in plaintext. Not much bother for you here, as your two machines are not on the net, but as a rule sane people don't use telnet, and I doubt you'll find it in synaptic. Ssh essentially is a secure replacement of telnet: it means "secure shell." What you did was install an ssh server on one machine, providing the means to "telnet securely" there from the other machine.
Ssh also has this very nice extension, called sftp (secure ftp) - you transfer files over ssh. This is what you actually used to browse one of your machines from the other one.
You can go to the command line and type:

ssh username@ipaddress

and you'll essentially telnet over ssh to the other machine, meaning you'll have the other machine's console. Ubuntu's file browser skips all that and makes the remote machine start sftp for you.

---

### Post by tomski on 2006-03-21
you are right about creating a root account and using webmin can be potentialy dangerous but that was method i used when i first encounterd linux and i did find it quite intuitive to use as a way to configure my system whilst i was getting to know the command line also i hate using sudo, 
so i suppose its down to user preference, we all start in different places

---

