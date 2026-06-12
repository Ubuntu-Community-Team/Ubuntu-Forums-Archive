---
title: "Constantly &quot;forgetting&quot; WEP key in Kubuntu"
date: 2006-03-23
forum: General Help
---

### Post by b00kwyrm on 2006-03-23
I've seen several places kinda deal with this issue, but I'm ready to really fix it if I can.

I'm using Kubuntu Breezy and at home I have a WEP enabled wireless router.  I'm currently using network-manager to connect because I has a lot of bad luck with KWifiManager, etc.  Anyway, it works flawlessly mostly.  Only problem is everytime I connect to my network, I have to re-enter the HEX WEP Key.  And, every so often, it forgets the key (while I'm still connected) and prompts me for it again.  

Note that no disconnects occur when I'm at school and no WEP key is required.  Also, when I run N-M in Gnome/Ubuntu, it doesn't lose the key.

Is there anything I can do?  Perhaps just saving the key in a file that I can point N-M to?  I just want it to work semi-automatically so I don't have to enable manually each time I switch networks.

Thanks!

---

### Post by Azrael on 2006-03-23
Open a terminal and type:

sudo gedit /etc/network/interfaces

Then add a line to the bottom of the text like so:

wireless-key 0123456789ABCDEF0152345678

You need to replace that key with your own of course (all attached, no colons). This might not be in itself not the most convenient solution if you use multiple wireless networks... (though you could create multiple versions of the interfaces file and create a script to automatically rename them or something)

EDIT: This only works if you bring the interface up before connecting. See the man pages for iwconfig and interfaces for more info.

---

### Post by ltmon on 2006-03-23
Azreal's anwer isn't correct.

If you are using networkmanager then the /etc/network/interfaces file should only contain your "lo" device.... nm will take care of the rest.

Make sure you have your device commented out in the interfaces file, else nm can get confused.  I had the opposite problem... I was running the network-manager daemon but didn't realise it.  It kept causing my static configured wireless to drop it's key.

Read the "notes" section on this page: [https://wiki.kubuntu.org/DapperNetworkManager](https://wiki.kubuntu.org/DapperNetworkManager)

L.

---

### Post by Azrael on 2006-03-23
[quote=ltmon]Azreal's anwer isn't correct.
[/quote]
I've never used this network manager, so yeah, I guess I should have checked that first... ](*,)

---

### Post by akshayas1986 on 2007-09-30
Hi
Even I seem to be facing the same problem. I have my Wifi networks WEP key stored in keyring manager. Yet once in a while, it keeps asking for the key. Dont know why.

---

