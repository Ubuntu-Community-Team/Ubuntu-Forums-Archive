---
title: "Help Installing emit"
date: 2012-04-02
forum: General Help
---

### Post by MadGeorge88 on 2012-04-02
I need help installing emit onto ubuntu so i can stream music to my android via wifi.

link [https://www.emitapp.com/](https://www.emitapp.com/)


please can someone help, new to ubuntu and it wouldn't buffer for vlc.

thank you

---

### Post by CynicRus on 2012-04-02
I see that this program exists under the android and the mac. How to run Mac - I don `t know, but that's about an android tell.
I'm not sure that the description of a way to completely solve the problem - but as a way of launching applications for android in ubuntu - is the place to be:

1) You need install android SDK, you may download SDK from here:[http://dl.google.com/android/android-sdk-linux_x86-1.5_r2.zip](http://dl.google.com/android/android-sdk-linux_x86-1.5_r2.zip)

2) In terminal: sudo apt-get install openjdk-6-jre , but you can install openjdk-7-jre . &#1042;o not think that this would be worse. The main thing - set the Java virtual machine.

3) After extract downloaded SDK:
cd ~/android-sdk-linux_x86-1.5_r2/tools
./mksdcard 2048M SDCard1
./android create avd -n *MyAndroidDevice* -t 2

4)create launch script:

```

#!/bin/bash
/home/*YOURUSERNAME*/android-sdk-linux_x86-1.5_r2/tools/emulator @*MyAndroidDevice* -sdcard /home/*YOURUSERNAME*/android-sdk-linux_x86-1.5_r2/tools/SDCard1

```*When using the format of how the home directory / SDK - 
I mean, it has been extracted to the you home directory

give some permission for launch to you script:
chmod +x myscript

5)Start youscript. Proffit.

Accordingly - your application must be placed on the virtual
 android device  - well, and use of health

---

### Post by rfs1970 on 2012-08-25
Hi MadGeorge88,

To properly install emit in your computer, you first need to install its dependencies:

sudo apt-get install miniupnpc libminiupnpc-dev

Once it finish, run the install script again as an administrator:

sudo sh ./install

---

### Post by XaRz69 on 2013-02-20
Hi rfs1970, 

I'm in oneiric. The install fails at sudo ./install because the libminiupnpc version is too old:

error: too many arguments to function ‘upnpDiscover’

(the libminiupnpc is version 5 in oneiric, and has only upnpDiscover with 4 arguments, and emit uses it with 6 arguments).

I can assume that emit needs precise or quantal for libminiupnpc updated versions?

---

### Post by slickymaster on 2013-02-20
You can find the full install instructions for Emit in Oneiric, [here]("http://pastebin.com/fQ0iifVC").

---

### Post by vinigfer on 2013-06-22
Did anybody ever made it installing emit server?
When I run emit -s I get the following error message:

sh: 1: exec: /home/vinicius/Downloads/priv/upnp: not found
{10,33,52} - <0.63.0> Upnp unknown msg {'EXIT',#Port<0.2688>,normal}
{"what":"state","portworks":false,"porttime":0,"upnp":false,"pin":["198","053","224"]}

I tried to install miniupnpc with make and make install commands, but aparently that didn't worked. What should I do to solve the problem?

---

