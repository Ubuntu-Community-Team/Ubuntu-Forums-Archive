---
title: "Can easily network using Hardy, can't with Jaunty....why?"
date: 2009-07-18
forum: General Help
---

### Post by ozguitarplayer on 2009-07-18
Hi,
I am trying to move from Hardy to Jaunty however networking with Jaunty stops this so I stay with Hardy.

I have 4 home computers networked using samba.
3 computers have Hardy Heron as the operating system.
1 computer was Interpid Ibex and is now Jaunty Jackalope .

All Hardy pc's network easily with each other after I install samba and select folders to share. I do nothing else.

When I tried to do the same with Intrepid and then Jaunty I cannot access the shares from any other computer, I get a 'unable to mount location'

I have tried to sort this on this forum before without success, most of the advice centres around /etc/fstab and mkdir, yet I don't need to do anything in Hardy with fstab and mkdir to get it to work.

I have followed all the much appreciated advice from others however it make no difference.

So I write again hoping that someone else may sort if from a different angle as I'm sure that fstab has little to do with it, as I said networking works straight up with Hardy, mind you I am a novice....
any suggestions please?

---

### Post by GandalfTheNerd on 2009-07-18
It's still easy, but has moved.  This fooled me for a while!  Just right-click on a directory in Nautilus to setup a share, and "Places/Connect to Server..." on the other machine to connect to it.  Works like a charm!

---

### Post by ozguitarplayer on 2009-07-18
thanks....however simple as it sounds I still don't get it as I can't find the "Places/Connect to Server.." should it be there on right click?

---

### Post by coffeecat on 2009-07-18
> **ozguitarplayer said:**
>  I can't find the "Places/Connect to Server.." should it be there on right click?

No, that's the Places menu between the Applications and System menus. Drop the menu down and 'Connect to Server' is below 'Network'. Alternatively, open a Nautilus window and go to File > 'Connect to Server'.

Some people are getting issues connecting to smb shares in Jaunty. I did on one machine, but not on another. Odd. Anyway, this thread should help you fix any problems you might encounter:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by ozguitarplayer on 2009-07-18
oh yeah right in front of me..thanks...now I need the server info; is this the path to the file e.g. /media/files or is it to do with the computer name?
I try all sorts and only get....Cannot display location "smb://xxx" though I'm sure it's to do with the information I've typing in.
Can you give me an example of what infomation is needed in the 'server' option please?

---

### Post by coffeecat on 2009-07-19
> **ozguitarplayer said:**
> Cannot display location "smb://xxx" though I'm sure it's to do with the information I've typing in.

Something like "smb://hostname/sharename/"

If that's what you're doing, it may be because your system isn't resolving the hostname. Check "Problem 3" in the link I gave and make sure the winbind daemon is running. Or try...

"smb://192.168.x.y/sharename/"

Obviously, substitute the actual IP address for '192.168.x.y' - your network might be using the 10.0.x.y range. If you need to use the IP address, it's easier if you set up all your hosts with fixed IP addresses, rather than relying on DHCP.

Finally, if you use "smb://192.168.x.y/" or "smb://hostname/" you'll get a choice of the shares on that particular host (if there's more than one) in the Nautilus window.

---

### Post by ozguitarplayer on 2009-07-28
hey coffeecat,
Sorry to resond so late. I found your reply in my junk folder.
Followed your lead and all is now as it should be, many thanks..

---

### Post by Scotty Bones on 2009-07-28
If you take coffeecats advice on using static IP's instead of DHCP. You should setup your Hosts file (/etc/hosts).

It should look something like this: (red represents the hosts on your network)

127.0.0.1	localhost
127.0.1.1	daedalus
[COLOR="Red"]192.168.1.42	atlantis
192.168.1.77	asuras
192.168.56.201	apollo
192.168.1.99	prometheus
192.168.1.98    odyssey[/COLOR]


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by ozguitarplayer on 2009-07-29
Thanks Scotty Bones,

Sounds weird I know but being new to this I've forgotten how to bring up the different IP addresses of my computers, can you remind me please?
I just looked and I don't have a /etc/hosts file, does this mean that I set one up and enter the different IP addresses as per your example?

---

### Post by Scotty Bones on 2009-07-29
No problem.

On Linux OS's you can find your IP address by typing ifconfig into the terminal, or right click the Network Manager tray icon and choose "Connection Information" . On Windows machines, use ipconfig in the command prompt.

You can check Network Manager to see if they are static or dynamically set.
Right click the nm tray icon> Edit Connections. Choose the proper tab ( ie. wired or wireless), if wired you should see something like eth0, for wireless you'll see Auto "SSID". select the connection you use and choose edit. Choose the IPv4 Settings tab. If method says "Manual", then you have a static IP. You'll see the IP listed under Addresses, along with the network mask and gateway.

The hosts file should be present already. try using this command in the terminal:
sudo gedit /etc/hosts

Of course, the hosts file is only useful if IP's are static. Don't list computers that use DHCP.


EDIT:
Some routers are capable of assigning static IP's based on MAC addresses. That would be the easiest way of assigning addresses to all machines at the same time, but a lot don't support that feature.

---

