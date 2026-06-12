---
title: "How do I install/enable LAN adaptor"
date: 2006-04-24
forum: General Help
---

### Post by sirdj on 2006-04-24
Hi I am an absolute newbie to linux, when I was installing Kubuntu, the installer correctly identified my wireless and LAN devices...but did not install it for some reason....now that the installation is complete, how do I install my LAN adaptor so that I can connect my wireless internet modem?
Secondly I do not have linux drivers for the wireless modem....any advise on the same? Can I use the mac drivers somehow?

---

### Post by gingermark on 2006-04-24
I'm not sure about mac drivers, but there is a utility called ndiswrapper which can allow many wireless cards to use Windows drivers. Have a look [here](https://wiki.kubuntu.org/SetupNdiswrapperHowto?action=show) for more info.

EDIT: Also note for part six of "Installing the Windows Drivers", instead of typing ```
sudo gedit /etc/modules
``` type instead ```
kdesu kate /etc/modules
```

EDIT AGAIN: [This page](https://wiki.kubuntu.org/WifiDocs/Driver/Ndiswrapper) might prove a better starting point, as it covers what you need to download using another computer (assuming you have no net access on yours).

---

### Post by sirdj on 2006-04-25
Thanks so much for your reply. BUt before I start doing things I thaught that I should just clarify stuff to be sure.

1) I own a Acer TravelMate 4152 NCLi.
2) My ethernet LAN adaptor is Broadcom 440x 10/100 Integrated Controller.
3) My wireless adaptor is Intel PRO/Wireless 2200BG Network Connection.
4) Both of these were correctly identified during installation, however something happened real fast on the screen and I did not note down exactly what(foolish of me on hindsight)
5) When the instalation was complete both these show up as eth0 and eth1 status = disabled
here is a screenshot of the network devices.
[Img]http://i3.tinypic.com/wgosgp.jpg[/Img]

6) If I try to enable or configure any of the devices, I am prompted for my password but not able to make any progress after that.
If I try to enable the device it enables for 1/2 a second and then goes back to the disabled status.
If I try to configure the device then i get a KDE Crash Handler - "The application KDE Control Module(kcmshell) crashed and caused the signal 11(SIGSEGV).

7) I tried to see the help pages and it says that I have edit the file /etc/modprobe.conf
but does not say exactly what to edit and how.
What should I do? Please help ! Anybody ?!!
here is a screenshot of the help pages
[Img]http://i3.tinypic.com/wgosqb.jpg[/Img]

---

