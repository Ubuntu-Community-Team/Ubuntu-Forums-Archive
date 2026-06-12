---
title: "Shared file through share tab.  Where is config saved?"
date: 2009-08-15
forum: General Help
---

### Post by Buttons840 on 2009-08-15
There is lots of information floating around on the net about Samba, much of which is out of date it appears.  I'm new, so I can't say for sure, but I have found a guide that is satisfactory, so any suggestions are appreciated.

When you right click a folder -> properties -> share tab, and set up sharing from here, it seems to work ok for me.  I've been able to share my Public folder using this GUI method (the share tab).

I installed samba client smbfs and server samba.  I then run the command:

```
sudo smbclient -L //127.0.0.1 -U bob
```

Which returns:

```
	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	IPC$            IPC       IPC Service (buttons-pcname server (Samba, Ubuntu))
	PSC-2350-series Printer   HP PSC 2350 series
	public          Disk      
Domain=[BUTTONS-PCNAME] OS=[Unix] Server=[Samba 3.3.2]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	HOMEWG               FAMILY
	WORKGROUP            BUTTONS-PCNAME

```

Notice samba sees the public folder is shared.

My question is where is that information stored?  It's not in the smb.conf.  smb.conf makes no mention of the public folder anywhere.

Again, I have 2 questions:
1) Any good samba guides you can suggest?
2) Where is the sharing config set through the GUI stored?

Thanks.

---

### Post by redmk2 on 2009-08-15
> **Buttons840 said:**
> There is lots of information floating around on the net about Samba, much of which is out of date it appears. 
 
Good that you have seen that early on. It is good practice to be dubious of information without documentation. In addition to information being out of date, be aware that there are differing flavors of Linux distro's. This can be confusing for new users.> 
 
I'm new, so I can't say for sure, but I have found a guide that is satisfactory, so any suggestions are appreciated.
 
I would start with samba.org's own site. Yes it is boring, but it is worth understanding how the system (Samba) works. Most of the doc's are at [_[COLOR=darkslategray]This location[/COLOR]_]("http://us1.samba.org/samba/docs/").

The one that I found very helpful was [_[COLOR=darkslategray]Samba By Example[/COLOR]_]("http://us1.samba.org/samba/docs/man/Samba-Guide/").> 
 
When you right click a folder -> properties -> share tab, and set up sharing from here, it seems to work ok for me. I've been able to share my Public folder using this GUI method (the share tab).
 
I installed samba client smbfs and server samba. I then run the command:
 
```
sudo smbclient -L //127.0.0.1 -U bob
```
 
Which returns:
 
```
    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    IPC$            IPC       IPC Service (buttons-pcname server (Samba, Ubuntu))
    PSC-2350-series Printer   HP PSC 2350 series
    public          Disk      
Domain=[BUTTONS-PCNAME] OS=[Unix] Server=[Samba 3.3.2]
 
    Server               Comment
    ---------            -------
 
    Workgroup            Master
    ---------            -------
    HOMEWG               FAMILY
    WORKGROUP            BUTTONS-PCNAME

```
 
Notice samba sees the public folder is shared.
 
My question is where is that information stored? It's not in the smb.conf. smb.conf makes no mention of the public folder anywhere.
 

All the config is handled by Gnome. The config files are at```
/var/lib/samba
```
 
I personally don't like using any Gnome configured settings in Samba. But then again my situation is for server based storage rather than a P2P solution.

---

