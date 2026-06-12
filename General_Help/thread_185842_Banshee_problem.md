---
title: "Banshee problem"
date: 2006-06-01
forum: General Help
---

### Post by playmobiel on 2006-06-01
Hi there

I would like to run banshee as my music player , i installed it via the repos but nuw when i try to start i get :
> 
Unhandled Exception: DBus.DBusException: Unable to determine the address  
of the message bus
in [0x0003e] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:46)               
DBus.Bus:GetBus (BusType busType)
in [0x00001] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:23)               
DBus.Bus:GetSessionBus ()
in [0x00007] (at                                                         
/build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/DBusIPC.cs:53)
Banshee.DBusServer:.ctor ()
in [0x00016] (at                                                         
/build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:135)  
Banshee.Core:.ctor ()
in [0x0000b] (at                                                         
/build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:73)  
Banshee.Core:get_Instance ()

btw : i have to notice that im runnig fluxbox on an ubuntu server installation , xmms works

Does anyone know what to do ? 

Thanks

---

### Post by playmobiel on 2006-06-03
no one knows?

---

### Post by frenkel on 2006-06-15
[QUOTE=playmobiel]no one knows?[/QUOTE]
Is dbus running? Try running > sudo /etc/init.d/dbus restart

---

