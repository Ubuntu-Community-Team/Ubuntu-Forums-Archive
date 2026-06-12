---
title: "Bad archive error"
date: 2011-02-04
forum: General Help
---

### Post by imgr8 on 2011-02-04
I am using apt-cacher for caching ubuntu packages for installation of client nodes on a network. When a PXE client starts, it sends requests to download files from the ubuntu archive online and I can see those requests in /var/log/apache2/access.log as :

"GET /3142/ubuntu//dists/lucid/Release HTTP/1.1" 404 511

I can see the problem is the "//" before dists as it should be just one slash. I followed the install guide at [http://terrarum.net/administration/automating-an-ubuntu-server-install.html](http://terrarum.net/administration/automating-an-ubuntu-server-install.html) for the apt-cacher settings and my ks.cfg file has url setting as :

[FONT=monospace]url --url [http://192.168.55.1/3142/ubuntu](http://192.168.55.1/3142/ubuntu)

Can anyone tell me where does the problem with the double slash lie? The PXE client gives "Bad archive mirror" error post this. Even if I don't use apt-cacher and just put 

url --url [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) 

in my ks.cfg file, I still cannot download the Release file from the ubuntu mirror. 

My [/FONT]/var/ftpd/pxelinux.cfg/default file is :

label linux
[INDENT]kernel ubuntu-installer/i386/linux
append initrd=ubuntu-installer/i386/initrd.gz ks=http://192.168.55.1/ubuntu/ks.cfg preseed/url=http://192.168.55.1/ubuntu/ubuntu-server.seed
[/INDENT]

---

