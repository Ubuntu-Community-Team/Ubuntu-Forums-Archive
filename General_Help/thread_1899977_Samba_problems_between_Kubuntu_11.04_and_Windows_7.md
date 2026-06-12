---
title: "Samba problems between Kubuntu 11.04 and Windows 7"
date: 2011-12-24
forum: General Help
---

### Post by ThomasMcA on 2011-12-24
I have googled, tweaked settings, searched this forum, and followed an old HowTo that I found on this forum. Nothing has worked, so I'm posting here.

I'm running a Kubuntu Natty 11.04 64bit laptop. I run Microcrap Windoze 7 in a VMWare Workstation VM. My Docs in the VM points to a Samba share on the Kubuntu host. The problem that I have is that the share is not available after starting Kubuntu unless I manually restart smbd before starting the VM. For example:

These steps don't work:
1) Start Kubuntu
1b) This command ps -e|grep mbd shows that smbd is running
2) Start the VM
2b) I can ping the host by name and IP, but I can't browse to it
2c) There are no errors in dmesg, or in /var/log/samba/
3) Windoze complains with **Error code: 0x80070043 The network name cannot be found.** 

As a workaround, all I have to do to fix this is manually run ```
sudo restart smbd
``` **before starting the VM**.

Before I restart smbd, ```
smbtree -d3
``` returns this:
Error connecting to 172.16.206.1 (Connection refused)
cli_start_connection: failed to connect to TOMLAPTOP<20> (172.16.206.1). Error NT_STATUS_CONNECTION_REFUSED

After ```
sudo restart smbd
```, ```
smbtree -d3
``` returns this:

```
Connecting to host=TOMLAPTOP
name_resolve_bcast: Attempting broadcast lookup for name TOMLAPTOP<0x20>
Got a positive name query response from 172.16.206.1 ( 172.16.206.1 )
Connecting to 172.16.206.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\TOMLAPTOP\IPC$                IPC Service (tomlaptop server)
                \\TOMLAPTOP\shared              My Shared Partition
```My ALSA information is located at [http://www.alsa-project.org/db/?f=a7f0be5fd70dd2b581b3188d81bd6781d9f61eee](http://www.alsa-project.org/db/?f=a7f0be5fd70dd2b581b3188d81bd6781d9f61eee)

Why would my connection problems be fixed by simply restarting smbd?

---

### Post by Nasair on 2011-12-24
I use stright Ubuntu for a file server, but use Xubuntu for my desktop for this reason. I had the hardest time just making simple shares. One trick which I didn't like, but did work for me was installing **Nautilus** and then setting up shares from the folder browser by right clicking and clicking on the share. Not sure how much this will help you but I was able to have a Windows 7 connect that way.

---

