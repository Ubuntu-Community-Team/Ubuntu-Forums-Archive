---
title: "Cannot browse Windows shares"
date: 2011-06-18
forum: General Help
---

### Post by kcstrom on 2011-06-18
I have been quite frustrated searching around for others that have had the same problems as I have had an what solutions are available.  It appears there is a plethora of issues surrounding file sharing between Ubuntu and Windows machines; but things work prefectly for some and not for others.

The specific problem that I have having is that I cannot access file shares from any of the Windows 7 machines on my network.  I use a Windows 7 machine for the main source of files that I like to access from other machines on the network.  I do not normally access it from other Windows 7 machines through a Homegroup (I have removed the Windows 7 PC from the homegroup while trying to figure this out as well) - I normally just browse the network via the Windows 7 machine.

Here is what I'm doing (and seeing):
1. Click on home folder icon on Unity's launcher
2. Click "Network" in the sidepane
3. Wait a long time (like 40 seconds or so).  "Windows Network" is the only folder/icon showing up in the "Network" folder once it shows anything.
5. Click on "Windows Network"
6. "WORKGROUP" shows up
7. Click on it
8. There is a delay with no visual indication (other than nothing happens and clicking in that window does nothing) and then I see "Opening "WORKGROUP" - Click cancel to stop"
9. See "Unable to mount location - Failed to retrieve share list from server"

I ran 'smbtree -N' and see a line for the PC I'm currently using, plus I see the following line for the other two PCs in the workgroup "WORKGROUP" (name is different for other PC):
```
     \\MEDIA-PC               
cli_start_connection: failed to connect to MEDIA-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```
I've seen guides to auto-mount certain shares from other projects to specific locations, and I'll probably do this at some point, but I really want to be able to browse the other machines shares.
```

session request to 192.168.1.3 failed (Called name not present)
session setup failed: NT_STATUS_LOGON_FAILURE

```


Does anyone have any idea why this isn't working and what can be done to fix it (assuming something can be done)?

Thanks.

---

### Post by garvinrick4 on 2011-06-18
Windows Workgroup is what you are using with samba in linux. It works right out of box
to see Windows machines as long as you have set Windows workgroup in Windows and made shares in Windows machine. If you want to see linux machine have to set what you
want to share in samba. But Ubuntu works out of box to see Windows workgroup using samba. Same for printer if you want to print from say a laptop to another machine with
USB printer that is Windows. When adding printer just use network printer using samba
in Windows workgroup.

Click on Windows workgroup instead of cancelling.

---

### Post by kcstrom on 2011-06-18
> **garvinrick4 said:**
> Windows Workgroup is what you are using with samba in linux. It works right out of box
to see Windows machines as long as you have set Windows workgroup in Windows and made shares in Windows machine. If you want to see linux machine have to set what you
want to share in samba. But Ubuntu works out of box to see Windows workgroup using samba. Same for printer if you want to print from say a laptop to another machine with
USB printer that is Windows. When adding printer just use network printer using samba
in Windows workgroup.

Click on Windows workgroup instead of cancelling.

Thanks for the response; but if it worked right out of the box, I would not have started a thread here.  I did not press cancel in the list in the original post, I was saying that a box came up with cancel - I let it keep going until I got the error message indicated.

---

### Post by garvinrick4 on 2011-06-18
> Thanks for the response; but if it worked right out of the box, I would not have started a thread here.
Ok, I was just trying to say that Looking at Windows machine is most likely way to resolve your problem. I have yet to have a install of Ubuntu not work in Windows Workgroup with Windows configured properly. Good luck partner and have a nice day.

---

