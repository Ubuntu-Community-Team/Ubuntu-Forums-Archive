---
title: "Best way to share files between two Ubuntu PCs?"
date: 2006-04-30
forum: General Help
---

### Post by oliver123 on 2006-04-30
Hello,

what is the best / preferred way to share files and folders between two PCs with Ubuntu Breezy on it? So far I tried Samba (but it requires some manual securing, and generally fails quite often to detect available PCs on the LAN) and NFS (which didn't offer any detection of available PCs).
So is there a third, better way? Will Dapper offer something for this task (mDNS / zeroconf / Avahi are pretty good for finding services, but will there be a sharing service, or maybe NFS integration?)

So far I use Samba with manually typing in the IPs (like smb://192.168.20.253) but this is very embarassing when a grinning Windows- or Apple-user is watching ;-)

Thanks in advance,
Oliver

---

### Post by Slim Odds on 2006-04-30
[QUOTE=oliver123]Hello,
So far I use Samba with manually typing in the IPs (like smb://192.168.20.253) but this is very embarassing when a grinning Windows- or Apple-user is watching ;-)
[/QUOTE]

Put a name for 192.168.20.253 in your host file and it won't be nearly so embarassing.

---

### Post by Ramses de Norre on 2006-04-30
sudo gedit /etc/hosts
Add a line to the upper section of the file with the ip adress of the machine you want to reach and a name for the machine (xxx.xxx.xxx.xxx name).
You can then type in that name instead of the ip adres.

---

### Post by oliver123 on 2006-04-30
Oh... /etc/hosts is a good idea :)

Now I'll only have to find a way to get this working with hosts with dynamic IPs (from DHCP or zeroconf)

Thanks for your suggestions!
Oliver

---

### Post by Jason_25 on 2006-04-30
If you prefer a GUI, places > network servers will do the same thing.

---

### Post by wylfing on 2006-04-30
[QUOTE=oliver123]So far I tried Samba (but it requires some manual securing, and generally fails quite often to detect available PCs on the LAN) and NFS (which didn't offer any detection of available PCs).[/QUOTE]

Erm, NFS doesn't really work that way. You have to explicitly configure NFS shares on the host system and explicitly mount them on the client system. You don't "browse" for NFS shares. Also, NFS is not often a good fit for machines that use DHCP to configure their networking.

So if you want to browse arbitrary shares on arbitrary computers, you're pretty much stuck with Samba. The flakiness of detecting available shares is essentially a property of SMB itself, because of its ad hoc nature. If you put Windows XP machines on a local network with, say, Windows 98 machines, you will notice the same thing. Half the time they can't see each other properly, or if they can see each other, they can't access shares properly. It's because they can't agree on things like who is the network master, and so on.

You could try tweaking the oslevel parameter so that one of your boxes is the undisputed network master. That might help.

---

### Post by nanotube on 2006-05-01
i would heartily recommend using ssh to transfer files between the two comps. put an ssh server on one, use an ssh client on the other. ssh client comes installed by default, and ssh server is just a quick apt-get install away (and no need for messing around with config, either - ssh-server gets installed in a very reasonable configuration).

---

### Post by Peter76 on 2006-05-07
Yes, use ssh; it is very safe, and in Dapper you can actually mount via ssh without any extra software. Really nice feature

---

### Post by ZylGadis on 2006-05-07
Also there is the extremely neat sshfs trick. Look for howto sshfs on the forums. That allows you to mount a directory through ssh and not have to copy over every file you want to use first.
I had a dilemma between NFS and Samba a while ago, same as you. Once I found out sshfs exists, I never looked back to either of those.

---

### Post by nanotube on 2006-05-07
[QUOTE=Peter76]Yes, use ssh; it is very safe, and in Dapper you can actually mount via ssh without any extra software. Really nice feature[/QUOTE]
works on breezy just as well. just do a "file>connect to server" from the nautilus menu. is it the same, or is there another fancier way to do it on dapper?

---

### Post by oliver123 on 2006-05-09
Thanks for the many replies! I'm currently looking at things like SFTP (which unfortunately doesn't work with service-discovery-applet atm.) and gnome-user-share (which uses WebDAV and is quite nice, apart from the heavy dependency on Apache, and apart from the slowness). Some days ago I also stumbled upon an Ubuntu spec / suggestion for this kind of problem, but now I can't find the link ](*,)

So, WebDAV or SSH/SFTP should be enough for me :) And if gnome-user-share or something similar goes into Dapper+1, that would be cool...

Thanks,
Oliver

---

### Post by dyssident on 2006-07-16
I use Avahi for naming, OpenSSH (sFTP) for file sharing and CUPS' IPP for printer sharing. IMHO they are the perfect combination. Once Gnome's Zeroconf support comes up to something useful, the perfection will be doubled, thereby making Ubuntu networking as easy as OSX's.

---

