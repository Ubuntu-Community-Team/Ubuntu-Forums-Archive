---
title: "How to run FreeNX server with PXE on Ubuntu using LTSP installation"
date: 2009-08-10
forum: General Help
---

### Post by zaikxtox on 2009-08-10
Hello. I have setup an ltsp server on ubuntu to work with a bunch of thin clieng machines without hard disk using PXE boot, but it was very high load for the network. With only four users where we experienced a lot of traffic, so i started looking for other ways to work.
Here i tell my experience on this subject.

The point is 

1) PXE boot to work on diskless stations
2) FreeNX or other lightweight system.

LTSP on ubuntu is very straightforward and is the first option to try. We install it by:

```
sudo apt-get install ltsp-server-standalone
```

Once we have it, the next step is to build our PXE image

```
sudo ltsp-build-client --arch i386
```

And then you have to edit the values on /etc/default/dhcp3-server and /etc/ltsp/dhcpd.conf

we restart dhcpd with 
```
sudo /etc/init.d/dhcp3-server restart
```

and we should have now everything working.

Try it booting booting PXE on other computer. Remember, if you have another dhcp server on the LAN you will have problems. You can tell the other dhcp server to work toghether, but first avoid complex things.

Once you have this working, we are going to modify our PXE image to use FreeNX instead of LTSP.

Step 1: Installing FreeNX server on the computer.

The way i used is the launchpad ppa repository. Follow instructions at [https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server](https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server)

Step 2: Download NX client.

I use Nomachine NX Client. It work great. I like it. download it from nomachine.com [http://www.nomachine.com/select-package-client.php](http://www.nomachine.com/select-package-client.php)
Download the 32 bit version deb package and move it to /opt/ltsp/i386/root/

Step 3: Chroot and installation of components.

You have to work now inside the ltsp image, so we are going to chroot into:

```
sudo chroot /opt/ltsp/i386/
```

That will give us a root shell on /opt/ltsp/i386/ system.
do:

```
cd /root
dpkg -i nxclient*.deb
apt-get install openbox
exit
```

We have installed nomachine NX client and openbox
now we are back and we have to do some things on the image dir. 

First, to avoid LTPS login manager to start we rename /opt/ltsp/i386/etc/rc2.d/S25ltsp-client-core to /opt/ltsp/i386/etc/rc2.d/s25ltsp-client-core

Then we create our own /opt/ltsp/i386/etc/rc2.d/S25nxclient with this content:

```
#!/bin/sh
su - root -c 'PATH=$PATH:/usr/X11R6/bin startx'
```

and make it executable with ```
sudo chmod +x /opt/ltsp/i386/etc/rc2.d/S25nxclient
```

and Third we chose our default X startup creating /opt/ltsp/i386/root/.xinitrc
with this content:

```
openbox &
while true;
do
/usr/NX/bin/nxclient
done;
```

So, then we rebuild the image with sudo ltsp-update-image

Now boot again the PXE client and will show the NoMachine NX client on an X server.
You are done!

Well... almost. Some tweaks:

1) Sound... install on the server the gstreamer0.10-esd and use the Enable Multimeda option on the NX client. The you have to configure gnome system to use ESD as sound.
2) Gnome Themes are gone? Ok... annoying, you have to do this hack: 

[http://aaron-kelley.net/blog/2009/08/freenx-on-ubuntu-9-04-jaunty-what-happened-to-my-gnome-theme/](http://aaron-kelley.net/blog/2009/08/freenx-on-ubuntu-9-04-jaunty-what-happened-to-my-gnome-theme/)

3) PXE client starts with NX Client unconfigured? Yes... you have to create a configuration connecting the server and then you copy the .nx config dir from that user to /opt/ltsp/i386/root 
It's not perfect, but works.

Well... hope someone find's it usefull. Here we made a very big change for our network with it. Clients run smooth and without eating all my ethernet links!

See you
Zaikxtox

---

### Post by tam3105 on 2010-03-18
Hi,
It is very interesting and fantastic one. we have configured it successfully with the help of steps given. I can able login in to the NX client.

Here, Could we use tsclient instead of NX client? Because we are using windows 2003 terminal server. we tried to configure tsclient instead of NX client, but it required lot of dependencies. we didn't know whether the steps what we did were correct or not.

It would be great support, if you help us. Thanks in advance.

---

### Post by rmainard on 2012-05-08
I know you posted this a while ago, but you can setup ltsp-cluster and specify rdp in the ltsp-cluster-configuration console. there is a how-to for cluster [here]("https://www.ltsp-cluster.org/documentation/howto/openvz-setup") Hope that helps, good luck.

---

