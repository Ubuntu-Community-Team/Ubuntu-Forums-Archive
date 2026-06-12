---
title: "Unable to install Sun JDK 6 on Ubuntu 10.04 64 bit server"
date: 2011-11-29
forum: General Help
---

### Post by nikhilpatwardhan on 2011-11-29
Hi,
I'm trying to install Sun JDK 6 on a machine(10.04 server 64 bit) and I get a[COLOR=Red] waiting for headers...[/COLOR] message for a long time after which the install aborts with the following messages. I have enabled the lucid partner repositories. This has been happening for so many days. The uname commands returns the following:  2.6.32-34-server #77-Ubuntu SMP Tue Sep 13 20:54:38 UTC 2011 x86_64 GNU/Linux. I would appreciate if someone could help me with the problem.

---------------------------------------------------------------------------------------------- 

sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-33-server linux-headers-2.6.32-33 linux-headers-2.6.32-34 linux-headers-2.6.32-34-server
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gsfonts-x11 java-common odbcinst odbcinst1debian1 sun-java6-bin sun-java6-jre unixodbc
Suggested packages:
  default-jre equivs binfmt-support sun-java6-demo default-jdk-doc sun-java6-source sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming libmyodbc odbc-postgresql tdsodbc unixodbc-bin
The following NEW packages will be installed:
  gsfonts-x11 java-common odbcinst odbcinst1debian1 sun-java6-bin sun-java6-jdk sun-java6-jre unixodbc
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.7MB/55.9MB of archives.
After this operation, 165MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
[COLOR=Red]Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-bin 6.26-1lucid1
  Connection failed
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-bin_6.26-1lucid1_amd64.deb](http://archive.canonical.com/ubuntu/pool/partner/s/sun-java6/sun-java6-bin_6.26-1lucid1_amd64.deb)  Connection failed[/COLOR]
-------------------------------------------------------------------------------------

---

### Post by BC59 on 2011-11-29
As I understand you have a problem with your main server. Go to Update Manager and in the lower left corner is the button of Software Sources. Open it and go to the first tab Ubuntu Software.

Go down to the Download from and scroll the button to Other.

Then choose your country and from the right upper corner Select Best Server. Wait until the system finds a working server and then select it by pushing the button Choose Server.

Update your system and try again to install Java.

---

