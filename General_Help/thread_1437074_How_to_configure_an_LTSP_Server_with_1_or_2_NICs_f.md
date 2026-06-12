---
title: "How to configure an LTSP Server with 1 or 2 NICs for Thin Clients."
date: 2010-03-23
forum: General Help
---

### Post by aliancemd on 2010-03-23
Hello.

- First of all, this article is based on this tutorial: [http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166).

- The second thing I want to say: You need Internet for this.

- 3-rd: You need at least 7 GB of memory on your Hard Drive(HDD/SSD...).

- 4-th: On this configuration all the RAM and HDD space will be taken from the Server. The Thin Client can work with no HDD and at least 128 MB Ram.


If you have 2 NICs(Network Interface Cards):

Some information about the network, may help:
Let's say we have 1 Router through which we get the Internet and his IP is 192.168.1.1 and the NetworkMask for the network is 255.255.255.0 that means he is on network 192.168.1.0 with the broadcast address 192.168.1.255, if the NetworkMask is 255.255.0.0 then the network will be 192.168.0.0 and the broadcast address 192.168.255.255. We have the DNS Server on the IP 192.168.1.10. And our IP for the interface connected to the Internet(Router) is 192.168.1.20 and it is out of the DHCP range of the router, it is important.

The Steps:

1. Install Linux Ubuntu 9.10 Desktop Edition (that's what I've used), u can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) .

2. Download the script I wrote: [http://ubuntuforums.org/attachment.php?attachmentid=151169&stc=1&d=1269366556](http://ubuntuforums.org/attachment.php?attachmentid=151169&stc=1&d=1269366556)

3. Go to Applications->Accessories->Terminal and write in the terminal "sudo su", it will ask you for the password for the current user that you configured when you installed Ubuntu, insert it. After that you enter the root mode.

4. Now write  "sh " and drag the file LTSP.sh into the terminal or write ~/Downloads/LTSP.sh , there it goes by default in the English version of Ubuntu. It will look something like this "sh "/home/[user]/Downloads/LTSP.sh" " or "sh ~/Downloads/LTSP.sh". Press Enter to start the script. Answer to the questions and that's all.



If you have 1 NIC(Network Interface Card): 

1. Install Linux Ubuntu 9.10 Desktop Edition (that's what I've used), u  can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) .

2. Download the script I wrote: [http://ubuntuforums.org/attachment.php?attachmentid=151170&stc=1&d=1269366556](http://ubuntuforums.org/attachment.php?attachmentid=151170&stc=1&d=1269366556)

3. Go to Applications->Accessories->Terminal and write in the  terminal "sudo su", it will ask you for the password for the current  user that you configured when you installed Ubuntu, insert it. After  that you enter the root mode.

4. Now write  "sh " and drag the file LTSP2.sh into the terminal or write  ~/Downloads/LTSP2.sh , there it goes by default in the English version  of Ubuntu. It will look something like this "sh  "/home/[user]/Downloads/LTSP2.sh" " or "sh ~/Downloads/LTSP2.sh". Press  Enter to start the script. Answer to the question and that's all.

[COLOR=Red]After the install you will NOT have Internet more on this interface because it now works as DHPC Server for the Thin Clients.[/COLOR]


Some things to know:

[LIST]
[*]To make Thin Client to launch from your LTSP Server you have to enter in BIOS(Usually, just after u start the computer u have to press Delete) and set in the boot priority in the 1-st place the Network Card, or LAN. If there is no name of your NIC or the "LAN" you need to search to enable Network booting or something like this. If you know that Network booting is activated you can boot from network without configuring first boot in BIOS, you can start the Boot Menu(Often one of this keys: F8, F10, F11, F12, ESC) and choose to boot from your Network Card or LAN.
[*]Each computer connected to the server eats/uses 128 MB Ram Minimum from the server, and each application that the Thin Client will launch will eat/use Ram from the LTSP Server.
[*]Minimum RAM Memory on Thin Client: 64 MB, it may work on 48 MB on older LTSP versions(LTSP 4 has less security, no ecryption and all this kind of beauty which LTSP 5 has, because of that the size of the files passed to the Thin client is smaller on LTSP 4). Some say u need minimum 128 RAM else it will lag hardly.
[*]It didn't worked for the Dell Thin Clients that I've tried to launch on it, their configuration was: Intel Pentium II 450 Mhz, 32 MB Ram, 4 MB Video. I think because of low graphics(correction: It was because of low RAM and it will never work on this amount of memory, even if u try to configure the boot files...). But it worked very well on powerful computers(and it can work on pretty weak computers).
[/LIST]



**[COLOR=Red]18/11/2010: I didn't tried the script on Ubuntu 10.10 but on 10.04 LTS doesn't work for sure. It doesn't work automatically but you can open the file and copy the commands line by line, they still work[/COLOR]**

---

