---
title: "help with this - accidental torrent"
date: 2009-10-05
forum: General Help
---

### Post by jackm5423 on 2009-10-05
I am curious as to the outcome of this possible scenario. 

Let's say that you turn your computer on and you are at someones house or at work.  

1) You open Transmission with torrents running (i.e. not paused) but they are not uploading or downloading since you haven't connect wirelessly or wired to the internet. 

2) Then you switch to another user profile on the computer to login under an administrator profile. (just using the fast user switcher GUI where both users stay logged in)

3) Then you hook up a network cable.  

My question is this:

A) IF a network connection is made on the administrator profile, would it automatically connect on the OTHER profile and start downloading and uploading torrents?

B) If yes to question A, then what kind of identifying info would go to the system administrator of the network?  Do torrent file names and other identifying info transfer easily?  Is it easy to see what you are downloading by an system admin. or is it more that they could tell certain ports are active?  

C) If there is a firewall on the network, does that make it more likely nothing uploaded or downloaded? (i.e. - if other sites like youtube are already blocked in the network)

D)If an active connection is not established on the administrator profile, is it still possible that a connection was made on the other profile and that the torrents started to transfer?

E) Is there a log file I can look at to see if a connection was made and what activity took place?

---

### Post by 3rdalbum on 2009-10-05
As far as I know, the torrents would start downloading under the original user account, because Transmission is running under the first user account, and Network Manager runs as root.

The system administrator would not be notified of the torrents running, but they would still be able to see that Transmission is running, and if they run "netstat" they will be able to see that the torrents are running too. The System Monitor would also show throughput. If Remote Desktop is running on the user account, the administrator could connect and discover the torrent program, or look under the user's Transmission settings file.

A firewall will generally stop incoming connection requests if they have not been explicitly allowed. Some firewalls can be set up to block outgoing connection requests on certain ports. If the firewall is set up to block incoming connections, and to block outgoing connections on the chosen Transmission port, then all Transmission's packets will disappear and it will neither send nor recieve any data. **It depends on the firewall rules.**

A plugged-in Ethernet cable will always give all running user accounts a network connection.

I'm sure there is a log file, but I don't know where it's located. You might need to run a daemon to log this.

I'm hoping this isn't your homework assignment, because it's against the rules to ask for help with your homework on Ubuntu Forums.

---

### Post by jackm5423 on 2009-10-05
> **3rdalbum said:**
> 
I'm hoping this isn't your homework assignment, because it's against the rules to ask for help with your homework on Ubuntu Forums.

Thanks for your help, and no, this isn't a homework assignment.

I guess what I'm wondering is a worse case scenario of accidentally plugging an ethernet cable in @ work for less than a minute before one realizes that the torrent program is working on the other profile and might try to connect.

What kind of identifying information about my personal computer shows up on the network when I plug into ethernet @ work?  Will the system admin. be able to know what might have been trying to download or upload for 30 seconds before the ethernet cord got yanked?

If there could be any chance one could get in trouble for the above scenario @ work?

Would that "blip" of 30 seconds to a min. of possible activity probably go unnoticed on a corporate network?

---

### Post by geirha on 2009-10-05
Very unlikely. If network traffic is logged, they might see some connections to the bittorrent tracker and/or common torrent ports, but they won't be able to see what torrents you are downloading/seeding. And it's doubtful anyone will notice, unless your seeding of the new Ubuntu 9.10 Karmic Koala beta iso torrent happens to get a lot of high speed peers for a prolonged period... then the boss may get annoyed when his WoW starts lagging.

---

### Post by jackm5423 on 2009-10-05
> **geirha said:**
> Very unlikely. If network traffic is logged, they might see some connections to the bittorrent tracker and/or common torrent ports, but they won't be able to see what torrents you are downloading/seeding. And it's doubtful anyone will notice, unless your seeding of the new Ubuntu 9.10 Karmic Koala beta iso torrent happens to get a lot of high speed peers for a prolonged period... then the boss may get annoyed when his WoW starts lagging.

I didn't think about that, but I guess the tracker might show up also...?

---

