---
title: "canon pixma mg5200 install problems, Ubuntu 10.10"
date: 2010-11-03
forum: General Help
---

### Post by op3studios on 2010-11-03
I downloaded the Debian driver packagefrom the Australian site that was said to work in 10.4.
set up won't launch.
I just switched to Ubuntu so I'm not much good with the terminal yet.
any help or education welcomed.

here's the first several lines of driver launch result:


C_version="3.40-1"

L_INST_COM_01_01="Command executed = %s\n"

L_INST_COM_01_02="An error occurred. The package management system cannot be identified.\n"
L_INST_COM_01_03="An error occurred. A necessary package could not be found in the proper location.\n"
L_INST_COM_01_04="Installation has been completed.\n"
L_INST_COM_01_05="An error occurred. Your environment cannot be identified as 32-bit or 64-bit.\nTry to install again by using the following command.\n"

L_INST_COM_01_06="An error occurred. The specified environment differs from your environment.\nTry to install again by using the following command.\n"

L_INST_COM_02_01="Usage: %s\n"

L_INST_COM_02_02="Uninstallation has been completed.\n"

L_INST_COM_03_01="[Package]\n"


L_INST_PRN_01_01="Register Printer\n"
L_INST_PRN_01_02="Next, register the printer to the computer.\n"
L_INST_PRN_01_03="Connect the printer, and then turn on the power.\nTo use the printer on the network, connect the printer to the network.\nWhen the printer is ready, press the Enter key.\n"

L_INST_PRN_01_04="Connection Method\n"
L_INST_PRN_01_05="USB\n"
L_INST_PRN_01_06="Network\n"
L_INST_PRN_01_07="Select the connection method.%s"

L_INST_PRN_01_08="Searching for printers...\n"

...more...

---

### Post by JLH02 on 2010-11-04
I just got the MG 5200 working on 10.04.  I haven't tried it on my 10.10 machine yet.  I'll take a shot at it and post results here.

---

### Post by JLH02 on 2010-11-04
I just installed it on Ubuntu 10.10 32bit without any problems (using wireless).  Printed a test page just fine.

Did you look at the installation instructions in the user guide from:[ http://support-au.canon.com.au/contents/AU/EN/0300409501.html]("http://support-au.canon.com.au/contents/AU/EN/0300409501.html")

The guide is the download at the bottom of the page.

Specifically, it lists the Ubuntu install instructions as:

For Ubuntu 10.04 
 1) Expanding the archived file and switching to the expanded directory
  ```
[user@zzz /yyy]$ tar zxvf cnijfilter-mg5200series-3.40-x-deb.tar.gz
[user@zzz /yyy]$ cd cnijfilter-mg5200series-3.40-x-deb
```  2) Installing the printer driver
  ```
[user@zzz /yyy]$ sudo ./install.sh
```I hope this helps.

---

