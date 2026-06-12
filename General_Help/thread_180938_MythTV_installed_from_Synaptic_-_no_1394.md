---
title: "MythTV installed from Synaptic - no 1394"
date: 2006-05-23
forum: General Help
---

### Post by Exile29 on 2006-05-23
I installed MythTV from Synaptic and tried to configure it to run with my firewire card (trying to capture video from my Motorola DCT-6200) and I get an error stating that firewire support has not been enabled and I need to recompile. :( 

I've searched around a bit and noticed that most people seem to have installed MythTV manually. Is a manul install the only way to enable 1394 in MythTV?

---

### Post by Exile29 on 2006-05-24
^^^^^^^^^^^
<Optimistic Bump>

---

### Post by msebast on 2006-06-20
The mythtv firewire support requires this library: libiec61883 
But that library is not available from ANY of the ubuntu repositories for ANY version of Ubuntu.
Since the dependancy is not available the ubuntu mythv packages have to be compiled without firewire.

It is probably also required to install an up-to-date version of libraw1394 and libavc1394 


Once those are succesfully built and installed for your system you will be able to build mythtv with the --enable-firewire option.

See here for more info on getting firewire working:
[http://www.mythtv.org/wiki/index.php/FireWire](http://www.mythtv.org/wiki/index.php/FireWire)

If you're going to compile mythtv you might as well build something newer then the obsolete 18.x packages that are in the Ubuntu repositories.

I managed to build all of the above as dapper drake packages for amd64. My builds also enabled XVMC Nvidia support in mythtv. 

I'm still fighting with getting firewire working properly. Mythtv hangs when using live tv to change the firewire to a channel that has encrypted output.

-Mike

---

