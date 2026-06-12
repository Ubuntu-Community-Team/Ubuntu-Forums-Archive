---
title: "Brother MFC-7340 printer - Network Issue..."
date: 2010-04-19
forum: General Help
---

### Post by Badcam on 2010-04-19
I believe that I've installed the Brother MFC-7340 correctly as per the installation instructions on the Brother website:


```
$ sudo brsaneconfig3  -q  |  grep SCANNER
[sudo] password for XXXXX: 
  1 SCANNER             "MFC-7340"          I:192.168.1.4:9101

$ dpkg  -l  |  grep  Brotherii  brmfc7340lpr
                          2.0.2-1                                    Brother MFC-7340 LPR driver
ii  brmfcfaxcups                          1.0.0-2                                    Brother MFC/FAX fax share function driver
ii  brmfcfaxlpd                           1.0.0-2                                    Brother MFC-FAX LPD driver
ii  brscan-skey                           0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan3                               0.2.9-1                                    Brother Scanner Driver
ii  cupswrappermfc7340                    2.0.2-1                                    Brother MFC7340 CUPS wrapper driver
$ 

```


The printer works fine, but I'm needing to get the Fax and Scanner working. Xsane can detect three devices, two of which are the Brother Scanner setup (just different names for the same device. As an aside, how do I remove one of these?):

[IMG]http://ubuntuforums.org/picture.php?albumid=1783&pictureid=6005[/IMG]

But then I get this error:

[IMG]http://ubuntuforums.org/picture.php?albumid=1783&pictureid=6006[/IMG]

I believe that the problem lies with the way the MFC is connected over the network. The printer is connected to a Belkin 2xUSB port print server which is at IP 192.168.1.4 and uses port 9101. There is a Brother QL-550 connected to the other Belkin USB port. The device URI I'm using for the printer is:

socket://192.168.1.4:9101

I'm not sure what other information I can give you, so please ask me for whatever it is you need to assist me further. I'd like to get both the Scanner and the Fax working if possible.

Thanks in advance.

---

### Post by plucky on 2010-04-20
> As an aside, how do I remove one of these?

Try ```
sudo brsaneconfig3 -r <Name of scanner>
```

See [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn2.html#2)

Good Luck

---

### Post by Badcam on 2010-04-20
Thanks Plucky.

I've removed the additional scanner.

Now, hopefully, someone will be able to help with the rest of it.

Cheers :)

---

### Post by Badcam on 2010-05-05
It is too early to bump? ):P

---

