---
title: "pinging hostnames and not IP addresses"
date: 2006-04-13
forum: General Help
---

### Post by Goonie on 2006-04-13
Hi guys

I'm mounting various windows shares on different machines and I can ping their IP addresses but not their names. Can anyone tell me what I need to do to fix that? 

When I use LinNeighborhood it finds the windows machines and correctly identifies them by name but when in console I can't mount the shares unless I specify their IP address.

Thx
Goonie

---

### Post by thantos on 2006-04-13
Are you sure that you are using the correct/complete hostname?

for instance, if you have a network, homenet.net, and a computer, comp1, I then the full hostname is: comp1.homenet.net

---

### Post by Goonie on 2006-04-13
well I'm using the same name I use to ping the machine from windows. 

If I go. *ping gooniewin* from a windows machine my windows fileserver responds just fine but if I type *ping gooniewin* in Ubuntu I get **ping: unknown host gooniewin** Here is the output from terminal running LinNeighborhood

root@goonielap:/home/goonie# LinNeighborhood
Usage: [-?|--help] [--usage] [-B|--broadcast BROADCAST-ADDRESS] [-f|--flags]
        [-U|--unicast STRING] [-M|--master-browser] [-R|--recursion]
        [-S|--status] [-T|--translate] [-r|--root-port] [-A|--lookup-by-ip]
        [-d|--debuglevel DEBUGLEVEL] [-s|--configfile CONFIGFILE]
        [-l|--log-basename LOGFILEBASE] [-V|--version]
        [-O|--socket-options SOCKETOPTIONS] [-n|--netbiosname NETBIOSNAME]
        [-W|--workgroup WORKGROUP] [-i|--scope SCOPE] <NODE> ...
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.1.33 bcast=192.168.1.255 nmask=255.255.255.0
Client started (version 3.0.14a-Ubuntu).
resolve_lmhosts: Attempting lmhosts lookup for name GOONIEWIN<0x20>
resolve_wins: Attempting wins lookup for name GOONIEWIN<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name GOONIEWIN<0x20>
name_resolve_bcast: Attempting broadcast lookup for name GOONIEWIN<0x20>
Got a positive name query response from 192.168.1.26 ( 192.168.1.26 )
Connecting to 192.168.1.26 at port 445
Domain=[KIRKJUTEIGUR] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name []
Connecting to 192.168.1.26 at port 139
Domain=[KIRKJUTEIGUR] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name []
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.1.33 bcast=192.168.1.255 nmask=255.255.255.0
Client started (version 3.0.14a-Ubuntu).
Connecting to 192.168.1.26 at port 445
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a0215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60080215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60080215
Domain=[GOONIEWIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name []
Connecting to 192.168.1.26 at port 139
Doing spnego session setup (blob length=16)
server didn't supply a full spnego negprot
Got challenge flags:
Got NTLMSSP neg_flags=0x628a0215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60080215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60080215
Domain=[GOONIEWIN] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
dos_clean_name []

Does it make any sense to you guys? Shouldn't I be able to ping the machine called gooniewin just as easily from Ubuntu as I do from Windows?

Goonie

---

### Post by dcstar on 2006-04-13
[QUOTE=Goonie]Hi guys

I'm mounting various windows shares on different machines and I can ping their IP addresses but not their names. Can anyone tell me what I need to do to fix that? 

When I use LinNeighborhood it finds the windows machines and correctly identifies them by name but when in console I can't mount the shares unless I specify their IP address.

Thx
Goonie[/QUOTE]
Install the winbind package and see if that helps.

---

### Post by PBK on 2006-04-13
I'm not sure you can mount this way (I don't see why it wouldn't, though), but you could add a line in your /etc/hosts file. The format is:

(remote IP address)          (computer_name) [alias_name]

  You can use whatever name you would like. Don't use the "()" or "[]". It really doesn't have to be the computers "given" name, but that's kind of what the alias part is about. That way when you enter a name in place of an IP address, the system first looks into the hosts file for help...

HTH

Paul

---

### Post by Goonie on 2006-04-14
dcstar:
I installed the winbind package and that had no effect.

PBK:
I know I can use /etc/hosts but that solution requires that I know the ip address of the machine I'm trying to ping (which I do in this case). What if I was on a large network and I only knew the computer names and needed to ping them? What does it take for Ubuntu to resolve the hostnames to an ip on the network?

Thx guys =)

Goonie

---

