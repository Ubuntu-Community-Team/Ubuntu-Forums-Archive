---
title: "Cant Use TFTP"
date: 2010-04-15
forum: General Help
---

### Post by shikhar_sharma on 2010-04-15
Hi Guyz,

I am sorry to post this topic but unfortunately i have spend over 2 days searching for a solution but couldnt find an answer.I am using ubuntu 9.10.I installed GNS3 perfectly and everything is working.Now i want to setup a tftp server.So i followed the instrucitons on 
[http://www.davidsudjiman.info/2006/03/2 ... in-ubuntu/]("http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/")
I cant understand the 2nd step.Do i have to create a directory by the name of tftp inside /etc/xinet.d and then place a file tftp inside it with all this script on step 2 or just a file in the /etc/xinet.d by the name of tftp with this script.What i did was i created a file tftp inside /etc/xinet.d and then when i started the xinet.d by the command 
$ sudo /etc/init.d/xinetd start
It says FAIL
but when i restart it using
$ sudo /etc/init.d/xinetd restart
its says OK
So does that mean i have configured the TFTP server?????
2nd problem is how the hell am i supposed to connect this tftp server to my router in GNS3.
if i type 
copy running-config tftp
then it asks for the TFTP address.I have connected my machine to tftp using a tap interface and i can ping the router from my terminal and vice versa.So if i enter the ip address of my tap interface then it says
TFTP: error code 2 recieved - 16739
%Error opening [tftp://192.168.10.1/router-config](tftp://192.168.10.1/router-config) (Permission denied)
But i started the xinet.d as a root.I am not sure what is the name or IP that i am supposed to use in the name of the TFTP server..Also please tell me what am i doing wrong.is this an incorrect procedure.
Also what is the difference b/w using a loopback and a tap interface.I wanted to do NAT/PAT thats why i thought that its better to use tap instead of loopback.PLZ help me out

---

