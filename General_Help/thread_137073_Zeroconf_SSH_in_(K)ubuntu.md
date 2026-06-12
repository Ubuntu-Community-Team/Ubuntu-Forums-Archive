---
title: "Zeroconf SSH in (K)ubuntu"
date: 2006-02-27
forum: General Help
---

### Post by hunger on 2006-02-27
Today I played a bit with zeroconf/bonjour/rendezvous in Kubuntu/Dapper. My goal was it to have the services usable via SSH advertised on my local network. 

I hope this applies to Breezy as well... The procedure requires some manual steps, so I thought I'd describe what I did here.

**Advertizing Services**

Install avahi-daemon to advertise the services a computer offers: ```
sudo apt-get install avahi-daemon
```

Check the configuration in /etc/avahi/avahi-daemon.conf. It was fine for me, and usually you should not need to edit it.

Now you got a avahi-daemon running. Unfortunately it does not yet know what to advertise.

One example configuration file can be found in /usr/share/doc/avahi-daemon/examples.

It is used to advertise SSH via avahi. Copy that to /etc/avahi/services as root:
```
sudo cp /usr/share/doc/avahi-daemon/examples/ssh.service /etc/avahi/services
``` and restart avahi-daemon with ```
sudo /etc/init.d/avahi-daemon restart
``` to have that service advertised. Gnome should pop up a notification telling you about the newly discovered service right after the restart. With KDE you need to point konqueror to "zeroconf:/" to see the newly discovered service.

If you have a packetfilter you need to configure it to allow UDP to/from port 5353 on both client and server IIRC. A packetfilter does not come with ubuntu by default, so if you managed to set it up you should manage to change it appropriately now;-)

Check [http://www.dns-sd.org/ServiceTypes.html](http://www.dns-sd.org/ServiceTypes.html) for an official list of services supported by bonjour. I announced the fish and sftp-ssh protocols in addition to ssh itself. Both services offer essentially the same remote file-access service and both work via the ssh-daemon.

To add Fish copy the ssh.service file to fish.service:```
sudo cp /etc/avahi/services/ssh.service /etc/avahi/services/fish.service
``` and edit it ```
sudo kate /etc/avahi/services/fish.service
``` (use gedit instead of kate in a gnome environment).

Replace the text between the "Remote Terminal on %h" with something more appropriate for FISH (i.e. "FISH to %h") and the "_ssh._tcp" with "_fish._tcp".

Do the same for sftp-ssh support, this time using "sFTP %h" for the name and "_sftp-ssh._tcp" for the type.

Restart avahi-daemon again for it to pick up your new services.

**Configuring KDE for zeroconfed FISH and sFTP**

In konqueror you should see your server in "zeroconf:/" now. Clicking on a server in the SSH subfolder should get you connected to it. Unfortunately konqueror does not know how to handle the FISH and SFTP links. To fix this install the files attached to malone bug #33034 ([https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/33034](https://launchpad.net/distros/ubuntu/+source/kdebase/+bug/33034)) into /usr/share/apps/zeroconf (of course you need to be root to copy them there). If you downloaded the files someplace cd there and run
```
sudo cp _fish._tcp _sftp-ssh._tcp /usr/share/apps/zeroconf
```

and revisit "zeroconf:/" in konqueror. It should now list proper icons in the FISH and sFTP folders and you should be able to connect to them now (assuming you current user can access the advertising server via SSH).

**Making normal Applications happy(er)**

Install the GLibC Bonjour Resolver library to enable non-bonjour aware applications to access the hosts in the virtual ".local" domain:

```
sudo apt-get install libnss-mdns
```

You will need to restart your applications for this change to take effect. One simple solution to get that is by logging out/in (or rebooting). Afterwards you can use your announced servernames as hostnames for all applications by appending ".local".

That's it. Works well for me... your mileage may vary of course.

---

### Post by Harry_Sack on 2006-02-28
Hey.
Thanks for this.

Just one thing.

In this line 
```
sudo cp /usr/share/avahi-daemon/examples/ssh.service /etc/avahi/services
```
you're missing "doc".

It should be
```
sudo cp /usr/share/doc/avahi-daemon/examples/ssh.service /etc/avahi/services
```
should't it?

Took me some time to figure out, cause I'm a noob you know.

---

### Post by hunger on 2006-02-28
You are right! I just fixed this issue. Sorry for the inconvenience.

---

### Post by el3ktro on 2006-03-11
I followed all your steps on Flight 5 - but when I start/restart avahi-daemon, nothing happens at all. I can see that SSH is announced then I do "avahi-browse -a" on the terminal though, but how can I now access this announced service trough Gnome? What am I missing?

Tom

---

### Post by hunger on 2006-03-11
I am not a gnome user myself, so I am no expert on how gnome does zeroconf. Some apps do it themselves, but I am not aware of something like zeroconf:/ in gnome.

You might want to try the service-discovery-applet (in universe). It seems to be quiet nice.

---

### Post by el3ktro on 2006-03-11
Yeah I also just found the service-discovery-applet, it's exactly what I was searching for. When it it started, I also see notification windows when a new service is discovered or when one is removed. Thanks!

Tom

---

### Post by haz2a on 2007-11-12
> If you have a packetfilter you need to configure it to allow UDP to/from port 5353 on both client and server - if you managed to set it up you should manage to change it appropriately now

Firestarter is easy to set up for most traffic, but can't be set in the GUI for multicasting as required by avahi. The rules most commonly suggested are:-
```
$IPT -A INPUT  -p udp --dport 5353 -d 244.0.0.251 -j ACCEPT
$IPT -A OUTPUT -p udp --dport 5353 -d 244.0.0.251 -j ACCEPT
```
These did not work for me in Firestarter v1.03 in Ub 6.10 or 6.06.

The rules below DO work in Firestarter v1.03 in Ub 6.10 and 6.06:-
```
$IPT -A INPUT  -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A OUTPUT -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A INPUT  -d 224.0.0.0/8 -s 0/0 -j ACCEPT
$IPT -A OUTPUT -d 224.0.0.0/8 -s 0/0 -j ACCEPT
```

Credit for these to Mike Pepe on the firestarter-user.lists.sourceforge.net see:- 
[http://ml.osdir.com/security.firewalls.firestarter.user/2006-04/msg00017.html](http://ml.osdir.com/security.firewalls.firestarter.user/2006-04/msg00017.html)

hunger - thanks for your guide on SSH via avahi.

---

### Post by haz2a on 2007-11-12
I should have explained that these rules need adding to the file /etc/firestarter/user-pre.

The complete procedure that DOES work for me in Firestarter v1.03, in both Ubuntu 6.10 and 6.06 LTS is:-
```
$ sudo -s
# cd /etc/firestarter
# chmod +w user-pre
# vi user-pre
Add the lines:-
$IPT -A INPUT  -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A OUTPUT -s 224.0.0.0/8 -d 0/0 -j ACCEPT
$IPT -A INPUT  -d 224.0.0.0/8 -s 0/0 -j ACCEPT
$IPT -A OUTPUT -d 224.0.0.0/8 -s 0/0 -j ACCEPT
# chmod -w user-pre
```

---

