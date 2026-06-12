---
title: "Ubuntu Server or Desktop? Sandy Bridge, Media Server, File Share"
date: 2011-03-15
forum: General Help
---

### Post by mebunto on 2011-03-15
Hello,
Some advice please ... I have been experimenting (successfully) with Maverick Server amd64 on my new Sandy Bridge motherboard (Gigabyte GA-H67MA-UD2H) with a Quad-core Intel 2600K chip and 8G RAM.
My question is simple ... should I use Ubuntu Server or Ubuntu Desktop?

I want to run the following main packages:

[LIST=1]
[*]Open-Iscsi
[*]Samba (I have a Drobo which I share across my home network, using the Linux box as the server)
[*]Mediatomb/Twonky with lots of different transcoders
[/LIST]
I like to use a GUI and install xorg-edgers .... so I've been post-installing Ubuntu Desktop on the server.  I also like to use the latest software, so I find using Natty attractive and I'm not too bothered about having to update/upgrade when the time comes.

Any good advice and humour is welcome!

---

### Post by mastablasta on 2011-03-15
if you plan to use it as server then use server edition. but for file sharing (samba) it can be desktop as well. 
Natty is still in alpha.

---

### Post by mebunto on 2011-03-15
OK thanks, I know that purists don't like to use the GUI, but is there any advice about using the GUI on Server?

---

### Post by Peter Alien on 2011-03-15
I'm using Ubuntu 10.04 LTS Desktop Edition as a server in my enterprise... but i tested the server version with only the GUI installed too.

What i found is that the only real difference is that the Desktop edition installs Ubuntu + GUI + Apps and the Server version with GUI installed after it, doesn't install the apps (most of them you don't need in a Server Operating System).

Runs cool and light :)

I have Samba, ufw, clamav and sbackup installed on it for now. The hosts are Win7 Professional and Home Premium Editions.

---

### Post by mebunto on 2011-03-15
Yes thanks - I think I'm going to see if I can get Natty server running with a GUI.  It didn't work last time I tried but it may work now.  Anyone know?

---

### Post by jerome1232 on 2011-03-15
My only thought is that doing a full blown Gnome Desktop Environment is overkill, If I was keen on using a gui I might install from the Ubuntu Server CD and then maybe install gnome-core to get the basic gnome desktop without the extra crap I don't need. Add a few apps here and there that I want.

I would probably not even use gnome give some other window managers a try, there's alot of good lightweight ones out there.

---

### Post by mebunto on 2011-03-30
Thanks everyone, I'm persevering with server and retrofitting gdm and kdm however the xorg drivers are a real pain.

---

