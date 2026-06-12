---
title: "Cannot mount samba share from DOS 6.22"
date: 2010-06-03
forum: General Help
---

### Post by micke.eskilander on 2010-06-03
Hi.

I know this might be an odd thread, but I'm struggling with an odd issue :)
We have a machine running DOS that we need to map towards a Ubuntu 10.04 machine running samba.
I have no issues mapping this samba share from any other machine.
Windows XP, Windows Vista and Windows 7 is all fine.
To be able to map from DOS, I know that "encrypt passwords" need tpo be disabled.
But other than that, I don't know if there are any other items that needs to be enabled/disabled to get this to work.

The share is nothing special. And I'm using the same user on the DOS machine aswell as on the Windows machine(s). So I know that the account is working.

The other strange thing, is that the current machine with the samba share that we are moving to the Ubuntu machine works like a charm.
On that machine, we are running Samba 2.05a.
Have tried that version, 2.2 and the latest available version on the Ubuntu machine, with no different result.

The result:
I use a "normal" 'net use' command for the mapping:
net use i: \\server\share <user> <password>

When changing server to the new server, the server is denying me access instantly.
Eventhough I have samba logging enabled, nothing is even written in the logs.
Not the samba server log itself, nor any log for the connecting machine.

I have monitored the switch port, and I can see that correct machine is connected.
When running tcpdump on the Ububtu machine, I can see that the DOS client IS connecting, but is denied access.

I really need some help on this one.

Share setup:
[share]
	  comment = share comment
	  path = /path/to/share
	  read only = no
	  public = yes
	  browseable = yes

Other than that, no strange things in the samba config.
Tried security=share, security=user but no change.

Again, Windows machines can without any problems access the share using the same 'net use' command.
When connecting from dos, instantly I get the following:
"no response from remote host"
"device i: not linked"

Please help! :)
Been bugging me for some time..

Thanks.

/micke

---

### Post by pricetech on 2010-06-03
While my limited DOS networking experience is pretty much covered in cobwebs, here's a few thoughts that crossed my mind.

I'd look at the two smb.conf files side by side and see if there was some "magic" setting that has been forgotten.

DOS doesn't have native support for TCP/IP and I'm sure you've crossed that bridge already, but I'd see if maybe there was a later version, or maybe just a different version, than what you have on the DOS client that might work.

Run smbpasswd on the Samba server to include specifically the username / password that you are using from the DOS box.

That's what comes to mind as stuff I would try.  Good luck with it and let us know how it goes.

---

### Post by JoelOl75 on 2010-06-03
For older versions of Windows (Pre-2000) you need to set this in your globals section of smb.conf file:

lanman auth = yes

---

### Post by micke.eskilander on 2010-06-04
Thanks for the replys.

I have "lanman auth = yes" in the config file.

<Run smbpasswd on the Samba server to include specifically the username / password that you are using from the DOS box.>
I am using the same username/password from a Windows machine, and that works.
I can also use 'smbclient -L server-ip' from another Linux box with the same username/password as on the DOS box and get positive results on the authentication.

The config from the old and working machine is identical to the Ubuntu machine.
Other than machine name and shared folder name.

Still not getting the DOS machine to authenticate...

Help is really appretiated.

Note: The Ubuntu machine is running on VMWare. Should that affect anything?

Thanks.

/Micke

---

### Post by JoelOl75 on 2010-06-07
> 
Note: The Ubuntu machine is running on VMWare. Should that affect anything?


Maybe... I don't think Windows shares traverse different subnets.  I think it's a layer 2 (MAC address, not IP) protocol.  If VMWare is setup to use its own subnet with NAT it may not work.  I believe it needs to be bridged onto the hosts network (Viewed as its own network card like br0)  I think this requires the bridge-utils package.  I might be wrong but an easy solution for you may be to use VirtualBox instead of VMWare.  I love VirtualBox and I know you can use VMWare images with it.  It may need setting adjustments to work though.  The version in the repos doesn't have USB support so I use the PUEL version downloaded from  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Sorry I can't help much... I remember bridging a virtual adapter wasn't the easiest thing to do (and getting it to survive a reboot).  There's guides all over describing problems with setting it up with vmware/ubuntu and guides about editing /etc/network/interfaces manually which means wicd and network-manager probably can't be used... Sounds less than promising to easily set up.

Virtualbox, even using NAT, can create shared folders. There's even examples on their site and in the instructions on how to do this in DOS.

Also could the 8.3 naming convention be part of the problem?

Just taking stabs in the dark at this point...Sorry.

---

