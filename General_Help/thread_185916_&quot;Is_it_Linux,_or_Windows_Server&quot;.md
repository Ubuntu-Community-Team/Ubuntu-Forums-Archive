---
title: "&quot;Is it Linux, or Windows Server?&quot;"
date: 2006-06-01
forum: General Help
---

### Post by leetcharmer on 2006-06-01
lawl, I like those ads ... but anyway -- here's the question: Dapper's out now; I have a PC that I want to turn into a webserver along with an LTSP server, which of the Ubuntu flavors should I go with?  I hear Edubuntu is good for the LTSP -- but Ubuntu has the server disk and what-not.  On this server box, I'd still like a GUI; it has the hardware to accomodate for one.  So, which is it? Ubuntu, Kubuntu, Edubuntu, Xubuntu? ... or Windows Server?

---

### Post by ronlybonly on 2006-06-01
Don't take me as the authority on this one - I have never installed Ubuntu for the server. But from what I've heard, any of them should do just fine. You may want to install from the server disk and then apt-get ubuntu-desktop|kubuntu-desktop|xubuntu-desktop. That's just my take, anyway.

---

### Post by David Corrales on 2006-06-01
Use the regular Ubuntu install disk, then just add the servers and use the kernel server. It's all the same code base.

---

### Post by leetcharmer on 2006-06-02
then just add the servers and kernel server?

apt-get install *what goes here*?

---

### Post by mattisking on 2006-06-02
Can't remember off hand exactly but if you use synaptic and look in "Base" you'll see a kernel version that ends in '-server'. I think that's about it.

---

### Post by apollyonis on 2006-06-02
```
sudo apt-get install ltsp-server
```

-for a LTSP server with DHCP already implemented (connected to router with DHCP, DHCP server installed)

```
sudo apt-get install ltsp-server-standalone
```

-for a LTSP with no DHCP access.

```
sudo apt-get install ltsp-util
```

-for LTSP setup utilities.

NOTE : Do not quote me on this - I haven't personally used LTSP, but these are the packages for it.

---

### Post by mcduck on 2006-06-02
You could also use the Server disk, as it includes an option to install LAMP server during the install, that would make the webserver part very easy..

> 
Automatic LAMP (Linux, Apache, MySQL and PHP)

In about 15 minutes, the time it takes to install Ubuntu Server Edition, you can have a LAMP server up and ready to go. This feature, exclusive to Ubuntu Server Edition, is available at the time of installation. 

The LAMP option saves the trouble of installing and integrating each of the four separate LAMP components, a process which can take hours and requires someone who is skilled in the installation and configuration of the individual applications. You get increased security, reduced time to install, and reduced risk of misconfiguration, all of which results in a lower cost of ownership.


---

### Post by joshrobinson on 2006-06-02
[QUOTE=mcduck]You could also use the Server disk, as it includes an option to install LAMP server during the install, that would make the webserver part very easy..[/QUOTE]

nice quote. answered questions of mine about the server edition.. note im not the person who started the thread.. just a random:D

---

### Post by leetcharmer on 2006-06-02
does anyone know how to make this server I plan on building an effective SAN / NAS server as well -- I've got about 1TB on it (multiple HDDs) with about 500GB on RAID.

Also, know of anyways that I can install it in this room, and then pop it in the server room next to the router and access it remotely for all the rest of my needs (there's no monitor in there)?

---

### Post by pek on 2006-06-02
and if i download the desktop version, wich is the command to get LAMP working? i know it's possible with the server version... just trying to spare some bandwidht and a cd :p

---

### Post by leetcharmer on 2006-06-02
what's the difference between "Install to Hard Disk" and "Install LAMP Server" on the Ubuntu Server CD?  Isn't that what would normally be installed on a Server anyway?

---

### Post by SSTwinrova on 2006-06-02
[QUOTE=leetcharmer]what's the difference between "Install to Hard Disk" and "Install LAMP Server" on the Ubuntu Server CD?  Isn't that what would normally be installed on a Server anyway?[/QUOTE]
Only if you were aiming for a webserver

---

### Post by leetcharmer on 2006-06-02
What else is there than a webserver that would come standard w/ the "Install to Hard Disk" method?

---

### Post by leetcharmer on 2006-06-02
[QUOTE=apollyonis]```
sudo apt-get install ltsp-server
```

-for a LTSP server with DHCP already implemented (connected to router with DHCP, DHCP server installed)

```
sudo apt-get install ltsp-server-standalone
```

-for a LTSP with no DHCP access.

```
sudo apt-get install ltsp-util
```

-for LTSP setup utilities.

NOTE : Do not quote me on this - I haven't personally used LTSP, but these are the packages for it.[/QUOTE]

I do have a router w/ DHCP setup; should I do ltsp-server & ltsp-server-standalone?  What's the difference between the two?

---

### Post by garyng on 2006-06-02
In general, you don't want to have 2 DHCP servers on the same network. However, if you don't use the ubuntu box as the DHCP server, you need to manage the other DHCP server beyond what it is now. So if it is a typical off the shielf router, that could be even more problematic.

I would just have 2 DHCP servers but make minor changes to the router to make it non-authoritive. Then you can manage the LTSP specific DHCP configs on the ubuntu box, much easier with more doc available.

---

### Post by nihilocrat on 2006-06-02
[QUOTE=pek]and if i download the desktop version, wich is the command to get LAMP working? i know it's possible with the server version... just trying to spare some bandwidht and a cd :p[/QUOTE]

Just install the software packages in a LAMP setup... i.e., Apache2, MySQL, and PHP. Make sure you install the apache2-php module and the php-mysql module so that they all cooperate. For a quick-and-dirty installation, I believe apt will automatically configure everything to recognize the modules.

---

### Post by leetcharmer on 2006-06-02
Okay, I've gone with the 'safe-route,' being that of Install LAMP from Server CD and then 'sudo apt-get install ubuntu-desktop.'  Is there documentation I can look at from there to make sure I get all the LAMP stuff running smoothely?  I'll work on the LTSP after I get LAMP up and running.  (I'm new to Linux Server Hosting ... what do I do after it's installed?)

---

### Post by garyng on 2006-06-02
pstree should tell you what process is running and you should at least see apache2 and mysql.


try to visit [http://localhost](http://localhost) which should also give you the apache testing home page.

But LAMP is really nothing but a skeleton, you need to put applications that use it and other than that, there isn't anything else to do.

---

### Post by tribaal on 2006-06-02
I installed the LAMP server setup today (via the server install disk), and I must say it's really brillant.

If you intend to deploy a professionaly LAMP server, you can do that in less than 30 minutes with this (starting from a factory clean machine), and it's really set up nicely.
I was able to install 6 LAMP servers in the same amount of time I would have taken to install only one without this disk...

The installation is minimal though, there is no GUI (which is what I wanted), and no bells and whistles (except for the very handy mysqladmin and phpadmin).


Just my 2c :)

- trib'

---

### Post by leetcharmer on 2006-06-02
> **garyng]pstree should tell you what process is running and you should at least see apache2 and mysql.


try to visit [http://localhost](http://localhost) which should also give you the apache testing home page.

But LAMP is really nothing but a skeleton, you need to put applications that use it and other than that, there isn't anything else to do.[/QUOTE]

yes! [http://localhost](http://localhost) popped up saying Apache was installed successfully

pstree shows this:
[QUOTE]init&#9472 said:**
> 
     &#9500;&#9472;atd
     &#9500;&#9472;bonobo-activati
     &#9500;&#9472;clock-applet
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dd
     &#9500;&#9472;dhclient3
     &#9500;&#9472;esd
     &#9500;&#9472;events/0
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;{evolution-data-}
     &#9500;&#9472;evolution-excha&#9472;&#9472;&#9472;{evolution-excha}
     &#9500;&#9472;firefox-bin&#9472;&#9472;&#9472;6*[{firefox-bin}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9472;&#9472;ssh-agent
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-cups-icon
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-panel&#9472;&#9472;&#9472;{gnome-panel}
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo&#9472;&#9472;&#9472;{gnome-vfs-daemo}
     &#9500;&#9472;gnome-volume-ma
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-keyb
     &#9474;                    &#9492;&#9472;4*[hald-addon-stor]
     &#9500;&#9472;hcid
     &#9500;&#9472;hpiod&#9472;&#9472;&#9472;{hpiod}
     &#9500;&#9472;khelper
     &#9500;&#9472;khpsbpkt
     &#9500;&#9472;kjournald
     &#9500;&#9472;klogd
     &#9500;&#9472;knodemgrd_0
     &#9500;&#9472;krfcommd
     &#9500;&#9472;ksoftirqd/0
     &#9500;&#9472;kswapd0
     &#9500;&#9472;kthread&#9472;&#9516;&#9472;aio/0
     &#9474;         &#9500;&#9472;ata/0
     &#9474;         &#9500;&#9472;ata_hotplug/0
     &#9474;         &#9500;&#9472;kacpid
     &#9474;         &#9500;&#9472;kblockd/0
     &#9474;         &#9500;&#9472;kgameportd
     &#9474;         &#9500;&#9472;khubd
     &#9474;         &#9500;&#9472;kseriod
     &#9474;         &#9500;&#9472;2*[pdflush]
     &#9474;         &#9500;&#9472;scsi_eh_0
     &#9474;         &#9500;&#9472;scsi_eh_1
     &#9474;         &#9492;&#9472;scsi_eh_2
     &#9500;&#9472;mapping-daemon
     &#9500;&#9472;mdadm
     &#9500;&#9472;metacity
     &#9500;&#9472;migration/0
     &#9500;&#9472;mixer_applet2
     &#9500;&#9472;mysqld_safe&#9472;&#9516;&#9472;logger
     &#9474;             &#9492;&#9472;mysqld&#9472;&#9472;&#9472;8*[{mysqld}]
     &#9500;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9500;&#9472;python
     &#9500;&#9472;sdpd
     &#9500;&#9472;shpchpd_event
     &#9500;&#9472;syslogd
     &#9500;&#9472;trashapplet&#9472;&#9472;&#9472;{trashapplet}
     &#9500;&#9472;udevd
     &#9500;&#9472;update-notifier
     &#9492;&#9472;watchdog/0


I see mysql in there :D -- so, are there any tutorials or docs to get me on my way to customizing this and turning this into a webserver the internet can see to host websites?

---

