---
title: "trouble saving open dns settings"
date: 2009-08-14
forum: General Help
---

### Post by 3pinner on 2009-08-14
ubuntu 8.10 - intrepid

I cannot seem to be able to save the settings for using open dns. I follow the instructions to the letter, and when I reboot, the settings are lost in Network connections. I need some help in editing a file that should save the settings even after reboot. 
the instructions are:

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ gksudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0

My Questions:
when I edit the dhclient.conf file, where do I append that line to the document?  - I found an existing line:
prepend domain-name-servers 127.0.0.1;
Do I just add it here at this line? - or do I add the line at the end of the document?

Also when I run the command:
$ sudo ifdown eth0 && sudo ifup eth0

I get the response
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.

Why?
What should I do when editing this the dhclient.conf file to get the settings to stick?

 I have tried running that set of commands, and editing the conf file a few times, and ultimately just went back into the conf file and removed the changes I made, so hopefully I'm back to ground zero and can start over.
Thanks for the help!

---

### Post by Iowan on 2009-08-15
> **3pinner said:**
> when I edit the dhclient.conf file, where do I append that line to the document?  - I found an existing line:
prepend domain-name-servers 127.0.0.1;
Do I just add it here at this line? - or do I add the line at the end of the document? I'd add it just below that line... and leave the original commented out (preceed with #).
Being unable to remember all the necessary steps for the ifdown/ifup combination, I usually just use **/etc/init.d/networking restart**.

---

