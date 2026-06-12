---
title: "transfer data from pc to laptop directly.."
date: 2010-08-15
forum: General Help
---

### Post by rahilm on 2010-08-15
hello everyone.  i have got a laptop for the first time that i'll be taking to college. I have a lot of data on my PC which i want to transfer to my laptop. My computer has Lucid 32bit while laptop has 64 bit installed,
Data is too much and transfering via usb drives will take a lot of time.. I do not know how to set up a network. Any help is appreciated..

---

### Post by slooksterpsv on 2010-08-15
On the computer you want to get your data onto go to: Places -> Home.

Create a new folder such as Shared, right-click on the folder you created and go down to Sharing options -> click on Share this folder and install Samba.

After that's all configured, log out and log back in.

Now on the other computer (the one you need data transferred from) open Places -> Home -> File -> Connect To Server -> Change to Windows Share -> and type in the name of the first computer (the one we're pulling data from) and click on Connect.

It should show you your share that we created on the computer we want the data to go to. Now just drag and drop everything you want copied over to that shared folder, then sort out.

Another method you could do (a little more dangerous) is share your *username* folder, and do it that way.

Let me know if you need anymore help ok?

---

### Post by Paqman on 2010-08-15
How much data do you need to transfer?

---

### Post by Ginsu543 on 2010-08-15
If you are trying to move a LOT of data, using Shared folders over the network can be a SLOW process. In that case, nothing beats an external hard drive with eSATA interface. If your laptop or pc doesn't have eSATA, then you can get an external drive with USB2.0 interface (many external drives have both specifications). IMHO, it's worth the investment to buy an external hard drive for file transfer and backup purposes.

---

### Post by rahilm on 2010-08-15
> **Paqman said:**
> How much data do you need to transfer?
around 250gb .. i have an external hard disk of 250gb which is already full... :P

---

### Post by Rinzwind on 2010-08-15
> **rahilm said:**
> around 250gb .. i have an external hard disk of 250gb which is already full... :P

Getting a 2nd external disc and filling that one up might be faster than copying it to your notebook ;)

---

### Post by Paqman on 2010-08-15
+1 for eSATA, although you can of course just plug any drive straight into the mobo on a desktop. eSATA just means you don't have to open the case up, in case those few seconds of your time are super-valuable ;)

---

### Post by rahilm on 2010-08-15
Sorry..I don't have a eSATA drive.. nor do i have the time to get one.. i m moving tomorrow. Plus, my PC does not have an eSATA drive (laptop has one)


> **slooksterpsv said:**
> On the computer you want to get your data onto go to: Places -> Home.

Create a new folder such as Shared, right-click on the folder you created and go down to Sharing options -> click on Share this folder and install Samba.

After that's all configured, log out and log back in.

Now on the other computer (the one you need data transferred from) open Places -> Home -> File -> Connect To Server -> Change to Windows Share -> and type in the name of the first computer (the one we're pulling data from) and click on Connect.

It should show you your share that we created on the computer we want the data to go to. Now just drag and drop everything you want copied over to that shared folder, then sort out.

Another method you could do (a little more dangerous) is share your *username* folder, and do it that way.

Let me know if you need anymore help ok?

A little confused here... just tell me if i am wrong..

I have a computer named : rahil-desktop
I have a laptop named : rahil-laptop
Since the only way i know of connecting computers is the LAN cable. I plug one end on my PC and one on my lappy,
Next, I create a new folder on my laptop named Shared. Right-Click->Sharing Options->Click shared->Install samba->logout->login

On my computer , i go to Places->Home->File->Connect To server->Windows Share
Then I type "rahil-laptop" in the server field.. and do nothing else..
This should theoretically work... I will test it and post if any errors..

---

### Post by rahilm on 2010-08-15
It gives the following error:
Cannot display location "smb://rahil-laptop/"
Failed to retrieve share list from server

---

### Post by Ginsu543 on 2010-08-15
You cannot connect two computers directly using a LAN cable. You must connect both computers to a router so that each computer can be assigned an IP address. Then when you set up your shared folder on one computer, it will be recognized by the other.

---

### Post by slooksterpsv on 2010-08-15
> **Ginsu543 said:**
> You cannot connect two computers directly using a LAN cable. You must connect both computers to a router so that each computer can be assigned an IP address. Then when you set up your shared folder on one computer, it will be recognized by the other.

Gah, I forgot to put that in my post.

You could try to set your ethernet connection to share to your computer. That may or may not work, usually it requires a patch cable to work

Usually, and this case doesn't always work, you would have to manually specify the ip addresses on the same subnet on both computers:
e.g. Laptop = 192.168.5.10 subnet: 255.255.255.0
Desktop = 192.168.5.11 subnet: 255.255.255.0
Then have desktop try to connect to 192.168.5.10 via Windows Share described above. It may or may not work. I've had both instances.

---

### Post by Paqman on 2010-08-15
> **rahilm said:**
> Sorry..I don't have a eSATA drive.. nor do i have the time to get one.. i m moving tomorrow. Plus, my PC does not have an eSATA drive (laptop has one)


You could just take the SATA drive out of your laptop and plug it straight into a SATA header on the desktop's motherboard. The connectors on laptop and desktop sized SATA drives are the same.

---

### Post by rahilm on 2010-08-15
> **Paqman said:**
> You could just take the SATA drive out of your laptop and plug it straight into a SATA header on the desktop's motherboard. The connectors on laptop and desktop sized SATA drives are the same.
My laptop is new i don't want to open it... 

> **Ginsu543 said:**
> You cannot connect two computers directly using a  LAN cable. You must connect both computers to a router so that each  computer can be assigned an IP address. Then when you set up your shared  folder on one computer, it will be recognized by the other.
OK. I'll empty some contents from my external hard disk. and do it by the old method..... :(

Sadly.. My ethernet router has only one slot for LAN cable and another for USB ..  which i suppose complicates matter...

---

### Post by HermanAB on 2010-08-15
Howdy,

You can easily make a 100Mbps cross over cable:
Take one ethernet jumper and cut it in the middle.  Strip the wires about 1/2 inch. Twist together again in cross-over fashion, and insulate with sticky tape:
Orange to Green
Green to Orange
Orange/White to Green/White
Green/White to Orange/White
Ignore the blues and browns (cut them short)

Now you can hook the two puters together directly and set the IP address, netmask and default gateway:
On one machine:
ifconfig eth0 192.168.1.1 netmask 255.255.255.255
route add default gw 192.168.1.2

On other machine:
ifconfig eth0 192.168.1.2 netmask 255.255.255.255
route add default gw 192.168.1.1

Now run vsftpd or sshd on one and connect with nautilus from the other.

---

### Post by Paqman on 2010-08-15
> **rahilm said:**
> My laptop is new i don't want to open it... 


The hard drive is usually ridiculously easy to get to, even on laptops. It's generally just a matter of popping one panel off. Two minutes work if you've got a nice small screwdriver.

---

### Post by slooksterpsv on 2010-08-15
Rahlim I noticed you marked this thread as solved, if you could let us know what you did to resolve the issue that way if others search for this problem they can say hey he did this and it worked, lets try it.

I'm curious on how you resolved it as well.

---

### Post by rahilm on 2010-08-16
> **slooksterpsv said:**
> Rahlim I noticed you marked this thread as solved, if you could let us know what you did to resolve the issue that way if others search for this problem they can say hey he did this and it worked, lets try it.

I'm curious on how you resolved it as well.
OOPS.. that was by mistake.. i wanted to add a subscription..
Unsolving..
nevertheless.. the thread is practically closed for me .. now that i have moved to college where there are obv no routers.. i used the old method (transfer via usb hard drives) because i thought that i would screw the connection at home..

Thanx for the help guys.. U r the best.!!:D

---

### Post by jv2112 on 2010-08-16
Option->

from your laptop you could use rsync and you can copy one home directory to the other.

Just set it up when you go to bed and it wont be so painful.

```

rsync -ave ssh name@IPaddess of Desktop:/home/name/ /home/name/


```

The second /home/name/ is the location of your laptop directory.

Also when you return home you can reverse it to update your desktop.

Just a thought.

---

### Post by scrooge_74 on 2010-08-16
> **slooksterpsv said:**
> On the computer you want to get your data onto go to: Places -> Home.

Create a new folder such as Shared, right-click on the folder you created and go down to Sharing options -> click on Share this folder and install Samba.

After that's all configured, log out and log back in.

Now on the other computer (the one you need data transferred from) open Places -> Home -> File -> Connect To Server -> Change to Windows Share -> and type in the name of the first computer (the one we're pulling data from) and click on Connect.

It should show you your share that we created on the computer we want the data to go to. Now just drag and drop everything you want copied over to that shared folder, then sort out.

Another method you could do (a little more dangerous) is share your *username* folder, and do it that way.

Let me know if you need anymore help ok?

No need to install samba, you can just go to Places > Connect to server > SSH 

give the info of the other computer (IP, user, folder) and you can log into it.

---

### Post by rahilm on 2010-10-09
I hope to reopen this thread after a long time.. i got back home.. and this time i hav a wifi router with me..
the connections are like ADSL Router - > Wifi Router -> (LAN Slots.. one going to my PC and another to a shared printer) Plus I use my laptop on Wifi NOw...

192.168.1.1 opens the ADSL router configuration while 192.168.1.2 opens the wifi router configurations..

I am now trying the above mentioned methods, hoping that they don't mess with my internet sttings..
If there is something extra to be done (like how to allot ip addresses) , plz bring to notice..
thnking you.

---

### Post by Alessandro.g89 on 2010-10-09
the wifi router should make things simpler. connect both computers to the internet and look at their local IPs (type "ifconfig" in a terminal). if you have 192.168.1.X on both, you should be able to share files between them directly, using either rsync, Samba or whatever

---

### Post by rahilm on 2010-10-09
done.
[slooksterpsv]("http://ubuntuforums.org/member.php?u=38762") solution worked.. (The first reply)
Thnx guys.. :)

---

