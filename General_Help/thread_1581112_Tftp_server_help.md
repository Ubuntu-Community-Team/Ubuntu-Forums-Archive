---
title: "Tftp server help"
date: 2010-09-24
forum: General Help
---

### Post by rgiles43 on 2010-09-24
Hello Everyone,

I have been trying to setup a tftp server but have had no luck. What would be the best tftp package to download if I am using the server to upload and save router configs? 

Yesterday I tried to install atftpd using :     sudo aptitude install atftpd
Yesterday I tried to install tftpd-hpa using:       sudo aptitude install tftpd-hpa

I had no luck in installing either of these two packages. 
I have verified that I am connected to the network by pinging google.com and getting a response. 

Also is there any extra packages that I need installed from TFTP to work?

Please let me know as this way I can tell which package to try to use.

Thanks,

---

### Post by rgiles43 on 2010-09-28
Hello,

I have installed atftpd using the following:

$ sudo apt-get install atftpd 
$ sudo vi /etc/default/atftpd[INDENT]USE_INETD=false OPTIONS="--daemon --port 69 --tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /var/tftp" [/INDENT]$ sudo invoke-rc.d atftpd start 
$ sudo mkdir /tftpboot 
$ sudo chmod -R 777 /tftpboot 
$ sudo chown -R root:root /tftpboot
$ sudo /etc/init.d/atftpd restart

However I get the following error when test the tftp as shown in the attachment:


Any help would be greatly appreciated.

Thanks,

---

### Post by rgiles43 on 2010-09-29
Any suggestions?

---

