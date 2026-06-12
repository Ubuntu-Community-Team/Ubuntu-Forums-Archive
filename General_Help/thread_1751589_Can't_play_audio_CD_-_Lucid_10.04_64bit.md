---
title: "Can't play audio CD - Lucid 10.04 64bit"
date: 2011-05-06
forum: General Help
---

### Post by HereInOz on 2011-05-06
Hi All,

I have been grappling with this for a month or so now, and hope you can help.

I preface this by saying that all other forms of CDs and DVDs work perfectly in this machine - the problem relates exclusively to Audio CDs, either burnt or bought.

When I put and Audio CD in the drive, the mounting process starts, takes longer than usual, and during this process, the desktop icons flash off then back on again, then the CD mounts and I get an icon on the desktop.

If I right-click and select Open, the desktop icons flash off and on again, and nothing else happens.

If I right-click and select Open with Rhythmbox, the same thing happens - desktop icons flash off and on, and nothing else happens.  Rhthymbox is not listed in the active processes either.

If I open Movie Player, and click on Movie in the menu, the Play disc 'Audio disc' option is greyed out.

If Rhythmbox is running, and I insert an Audio CD in the drive, Rhythmbox crashes and won't start again until I remove the Audio CD, then all is well again.

When I select Eject to remove the Audio CD, the desktop icons flash off and on again, then the CD ejects.

Apart from that, all is fine :-)

Hope someone has a solution.

---

### Post by nothingspecial on 2011-05-06
I recognise that dog :-k:P

What does dmesg say?

---

### Post by HereInOz on 2011-05-06
Thanks for the feedback and suggestion.

This is an extract from dmesg with things which probably pertain to the problem;

 end_request: I/O error, dev sr0, sector 56
[12371.793635] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.793639] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.793642] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.793647] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
[12371.793655] end_request: I/O error, dev sr0, sector 56
[12371.800262] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.800267] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.800271] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.800275] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
[12371.800284] end_request: I/O error, dev sr0, sector 56
[12371.806213] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.806217] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.806220] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.806225] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 0e 00 00 02 00
[12371.806233] end_request: I/O error, dev sr0, sector 56
[12371.811817] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.811820] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.811824] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.811828] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 1e 00 00 02 00
[12371.811835] end_request: I/O error, dev sr0, sector 120
[12371.817049] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.817053] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.817057] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.817061] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 1e 00 00 02 00
[12371.817069] end_request: I/O error, dev sr0, sector 120
[12371.822233] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.822236] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.822240] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.822244] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 1e 00 00 02 00
[12371.822252] end_request: I/O error, dev sr0, sector 120
[12371.826770] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.826774] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.826778] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.826782] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 1e 00 00 02 00
[12371.826790] end_request: I/O error, dev sr0, sector 120
[12371.830975] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.830978] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.830982] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.830987] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[12371.830995] end_request: I/O error, dev sr0, sector 0
[12371.834843] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.834847] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.834851] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.834855] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[12371.834863] end_request: I/O error, dev sr0, sector 0
[12371.838346] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12371.838349] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12371.838353] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12371.838357] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00

There are many more of these in dmesg but they are all the same kind of error.  Looks like the system doesn't like audio cd tracks for some reason.

Also found this further down dmesg output:

[12390.568482] rhythmbox[11222]: segfault at 28b500a ip 00007fbd8fdee01f sp 00007fbd83a65a40 error 4 in libbrasero-media.so.0.2.0[7fbd8fddb000+24000]
[12408.471200] rhythmbox[11250]: segfault at 7f7cd819a006 ip 00007f7cdd9f322b sp 00007f7cdcbdea40 error 4 in libbrasero-media.so.0.2.0[7f7cdd9e0000+24000]
[12427.233597] nautilus[11269]: segfault at 7f2d5004300c ip 00007f2d4b3e601f sp 00007f2d4464fa20 error 4 in libbrasero-media.so.0.2.0[7f2d4b3d3000+24000]

Any ideas?

By the way, the dog has been around - she could have been yours at some stage :-)

---

### Post by nothingspecial on 2011-05-06
Sorry kt, that's beyond me.

The search engine looks bad also.

........hoping for a hardware guru..........

---

### Post by HereInOz on 2011-05-06
Not really a solution, but I found the problem was within Brasero.  Un-installing Brasero fixed the problem; re-installing it caused the problem to return.  Hmm.

Installed K3b and the problem stayed away.  Looks like it is K3b for the life of this installation now.  That's not a bad thing, I guess.

Thanks for the help, nothingspecial, it clued me up on the problem Brasero was causing.

---

