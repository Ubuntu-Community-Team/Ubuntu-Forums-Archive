---
title: "Googleearth on insatll says check your internet connection"
date: 2011-10-29
forum: General Help
---

### Post by Peterfc on 2011-10-29
Hi

I have put a clean install on my Advent laptop. I have downloaded Google Earth. Before i tried to install Googleearth i used Synaptic manager to install the " utility to automatically build a Debian package of Google Earth " Then i tried to Install Googleearth by clicking on the downloaded file. After the Software manager opens i click install. Just after the start of the install it stops and a message saying Check your internet connect. I am in an internet cafe with 20mg connect.

I have spent a lot of time checking Google earth using the search but i can't find the answer.

Thanks for taking the time to read my problem.

Advent Laptop 250gb harddrive, 3gb ram

---

### Post by dcstar on 2011-10-30
> **Peterfc said:**
> Hi

I have put a clean install on my Advent laptop. I have downloaded Google Earth. Before i tried to install Googleearth i used Synaptic manager to install the " utility to automatically build a Debian package of Google Earth " Then i tried to Install Googleearth by clicking on the downloaded file. After the Software manager opens i click install. Just after the start of the install it stops and a message saying Check your internet connect. I am in an internet cafe with 20mg connect.

I have spent a lot of time checking Google earth using the search but i can't find the answer.

Thanks for taking the time to read my problem.

Advent Laptop 250gb harddrive, 3gb ram

Just go to the GoogleEarth website and download and install the .deb package.

---

### Post by Peterfc on 2011-10-30
Hi Dcstart

That's just what i did. When i click on the package Ubuntu Software Centre opens and when i use the option to install after a few seconds an error message opens saying to Check my Internet Connection. At the time i was in an Internet cafe. After a speedtest the result was 16.6mb download so i know the connection speed was ok. I also tried to install Miro but again i got the same answer. I am using Unity and have used the Forum to get Synaptic manager installed. When i used Synaptic manager to install Miro it worked fine. Also the same for Vlc. It seems my problem is with the Software Centre.

Thanks

---

### Post by dcstar on 2011-10-31
> **Peterfc said:**
> Hi Dcstart

That's just what i did. When i click on the package Ubuntu Software Centre opens and when i use the option to install after a few seconds an error message opens saying to Check my Internet Connection. At the time i was in an Internet cafe. After a speedtest the result was 16.6mb download so i know the connection speed was ok. I also tried to install Miro but again i got the same answer. I am using Unity and have used the Forum to get Synaptic manager installed. When i used Synaptic manager to install Miro it worked fine. Also the same for Vlc. It seems my problem is with the Software Centre.

Thanks

If you are in an "Internet Cafe" then you may need to change the Proxy settings so all dependencies for Googleearth can be downloaded and installed.

Use Synaptic to manually install the **ia32-libs** and **lsb-core** packages and try again.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/545134](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/545134)

---

