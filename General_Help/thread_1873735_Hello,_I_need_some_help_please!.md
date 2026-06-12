---
title: "Hello, I need some help please!"
date: 2011-11-01
forum: General Help
---

### Post by TopGigzter on 2011-11-01
Hello everyone, i am brand new here but have been reading up on Ubuntu for the last several weeks now, but my biggest problem is deciding what type of setup i need with Ubuntu, so i figured maybe i could get some help here. This is what my goals are for my new server and the specs of the machine i plan to use for the Ubuntu box. Please correct me if i leave anything out as im still learning....

My main goals are as follows:

1) be able to run several windows based applications/tools from the server
2) Be able to host a web page or site
3) Have the ability to store various files/folders ( given)
4) Be able to access those various files/folders remotely from another pc
5) Ability to allow my partner to remotely add or remove files from the server VIA FTP or 
    some type of GUI.
6) Basically i would like a setup similar to what you see on commercial server like Host
    Gator where you have a cPanel or something similar to control the server with.
The above requests are the most important features to me for this server, but im just not sure what "type" of server i should setup and with what extra applications, so i am open to any and all suggestions. If im not mistaken, would i need some type of virtulization application, or am i mistaken? Anyways, i need some guidance and tutorials if possible as well as what applications i need to install extra. Maybe im asking for something impossible, but as i stated, i am just learning Ubuntu and am willing to learn anything required to get this server setup. I will also post my pc specs below just in case it makes a difference. I really appreciate any and all help guys, Thanks in advance!

AMD 2.8Ghz
2GB DDR3
2TB WD Cavier Black 7200 RPM SATA
DSL Connection
Linksys Wireless Router

Regards, Stephen:(

---

### Post by killermist on 2011-11-01
> **TopGigzter said:**
> 
The above requests are the most important features to me for this server, but im just not sure what "type" of server i should setup and with what extra applications, so i am open to any and all suggestions. If im not mistaken, would i need some type of virtulization application, or am i mistaken? 
With the multiple and varied things you want to do, virtualization may be necessary.
> **TopGigzter said:**
> 
My main goals are as follows:

1) be able to run several windows based applications/tools from the server
2) Be able to host a web page or site
3) Have the ability to store various files/folders ( given)
4) Be able to access those various files/folders remotely from another pc
5) Ability to allow my partner to remotely add or remove files from the server VIA FTP or 
    some type of GUI.
6) Basically i would like a setup similar to what you see on commercial server like Host
    Gator where you have a cPanel or something similar to control the server with.

AMD 2.8Ghz
2GB DDR3
2TB WD Cavier Black 7200 RPM SATA
DSL Connection
Linksys Wireless Router


Items 2-5 could potentially be handled by the BSD NAS distro FreeNAS.  Though, I think the web server probably doesn't handle server-side scripting.
Item 1 may not be possible from Linux, and may require a (virtualized) windows instance.  If you've already got a windows machine, I'd use it for the tasks requiring windows.  Your call though.
Item 6 may cost money, as a commercially licensed product, not sure.

Those elements, taken as groups to be tasked to virtual machines could be hosted on a ProxmoxVE install on the bare metal hardware.  Then one VM could be FreeNAS, one a windows application/terminal server or whatever, and maybe 1 instance as a LAMP server if the webserver in FreeNAS can't handle your needs.

The specs you provided would make a good VM host for 2-3 servers (the ram will be the limiting factor for those probably) with plenty of storage, but I wouldn't try to serve much (if anything) to the internet on a DSL connection.

References:
FreeNAS  (I prefer the lower hardware requirements of "legacy" to the newer versions)  [http://wiki.freenas.org/](http://wiki.freenas.org/)
ProxmoxVE (essentially Debian64 preconfigured and optimized for VM hosting) [http://pve.proxmox.com/](http://pve.proxmox.com/)
LAMP (Linux, Apache, MySQL, PHP) [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

That's my $0.02 (which after inflation and taxes may only be worth $0.01)

---

### Post by coldraven on 2011-11-02
> 6) Basically i would like a setup similar to what you see on commercial server like Host
    Gator where you have a cPanel or something similar to control the server with.
I have only just started experimenting with servers so I am not an expert but would Webmin do item 6?

[http://www.webmin.com/index.html](http://www.webmin.com/index.html)

---

### Post by mastablasta on 2011-11-02
there is an interesting Ubuntu based distribution for small businesses server: [http://www.zentyal.com/](http://www.zentyal.com/)
 
most of the things you wrote can easilly be done with Ubuntu just as well. you will need to install LAMP which is a few clicks away after you install (or is it just use) tasksel
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)
 
this is for the web part of things. 
 
Now the problematic part is running windows based applications/tools from the server. what kind of applications? Are there any linux alternatives? even if there is virtualisation option possible is it necessary?

---

### Post by linuxwin2 on 2011-11-03
1) be able to run several windows based applications/tools from the server
-- What's you application, you can use Wine/Crossover or Virtualbox
2) Be able to host a web page or site
-- You can use Apache, Ligthhttp,nginx
3) Have the ability to store various files/folders ( given)
-- 
4) Be able to access those various files/folders remotely from another pc
-- You can access with ssh / vnc
5) Ability to allow my partner to remotely add or remove files from the server VIA FTP or some type of GUI.
-- use vsftp sever

---

