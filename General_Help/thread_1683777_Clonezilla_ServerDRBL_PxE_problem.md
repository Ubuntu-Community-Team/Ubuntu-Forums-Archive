---
title: "Clonezilla Server/DRBL PxE problem"
date: 2011-02-08
forum: General Help
---

### Post by Frapple on 2011-02-08
Good morning all,

Massively new to Linux, just set up DRBL/Clonezilla on Ubuntu 10.10 x64 according to a few guides/videos out there all seems well.

Ran sudo /opt/drbl/sbin/dcs on the server, went through all the options to set a certain client (template machine) to clonezilla-save-disk. (/opt/drbl/sbin/drbl-orc -b -q2 -j2 -p -poweroff -z1 -10000000 -h "10.0.20.102" -l en_US.UTF-8 startdisk save 2011-02-07-14-img sda)

But when booting to PxE the machine displays this.

[http://img130.imageshack.us/img130/4540/img2011020700019.jpg](http://img130.imageshack.us/img130/4540/img2011020700019.jpg)

I tried changing the /opt/drbl/sbin/dcs to 'select_in_client' but still receiving the same error.

Before I ran the first command, a PxE boot did take it to an Ubuntu login screen if that means anything.

If anyone has any clue what I can try or where I can post for help it would be most appreciated.

Thanks in advanced, Rob.

---

### Post by sisyphus1978 on 2011-02-08
I can't help with the error, but when I set up my own clonezilla/drbl pxe server I followed [this guide]("http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/").

Also DRBL and Clonezilla both have forums you could try out.

It is a little complicated, but once you get it sorted it is a god's send!

---

