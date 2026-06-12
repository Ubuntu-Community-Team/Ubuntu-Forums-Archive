---
title: "Where is LDM on LTSP"
date: 2009-10-05
forum: General Help
---

### Post by steviefordi on 2009-10-05
I have recently setup a virtual network using VMWARE, installing an LTSP server and setting up some low powered machines to boot from the server. I was proving the concept to my boss - the IT Manager - (who is windows user through and through) that our call centre could run on this platform.

I put it to him that it would breathe fresh life into around 100 otherwise 'dead' Windows 2000 machines we have, and significantly decrease the cost of expansion by buying in diskless workstations rather than fully fledged PC's - not to mention the ease of administrating all users files.

Good news is the proof of concept worked and he's totally sold on the idea of going with Ubuntu (put anything to a business in terms of money and they will listen!).

However, when I login from a remote station to the system, I am running the Gnome Desktop. All the documentation I read suggests I should be running LDM. Is this something new that is undocumented? Or have I added the users incorrectly (I did it on the server through "System >Admin >Users and groups")?

Any info on this would be greatly appreciated.

---

### Post by steviefordi on 2009-10-08
bump

---

### Post by fairplay89 on 2011-02-14
> **steviefordi said:**
> I have recently setup a virtual network using VMWARE, installing an LTSP server and setting up some low powered machines to boot from the server. I was proving the concept to my boss - the IT Manager - (who is windows user through and through) that our call centre could run on this platform.
 
I put it to him that it would breathe fresh life into around 100 otherwise 'dead' Windows 2000 machines we have, and significantly decrease the cost of expansion by buying in diskless workstations rather than fully fledged PC's - not to mention the ease of administrating all users files.
 
Good news is the proof of concept worked and he's totally sold on the idea of going with Ubuntu (put anything to a business in terms of money and they will listen!).
 
However, when I login from a remote station to the system, I am running the Gnome Desktop. All the documentation I read suggests I should be running LDM. Is this something new that is undocumented? Or have I added the users incorrectly (I did it on the server through "System >Admin >Users and groups")?
 
Any info on this would be greatly appreciated.
 
I was wondering if you ever figured this out. I am trying to do the same thing for my college. Any answers would be appreciated. Thanks!  :)

---

### Post by steviefordi on 2011-02-17
I have figured this out, but not at the time I was trying to. Basically, when I wrote this post, I didn't understand what a display manager was (LDM is a display manager). I was slightly confused between that and a desktop environment.

A display manager is the application that enables a graphical login - as opposed to a text based one. I believe (although I'm not 100% sure) that it is responsible for loading the graphics card drivers. It does this prior to login so it can present you with a graphical login screen for your credentials. Once you login, it will run the desktop environment.

A normal desktop Ubuntu install uses the Gnome Display Manager (GDM). If you've ever played with your graphics drivers you would normally have to do something like...

```
sudo /etc/init.d/gdm stop
```

to run a script that unloads the desktop, graphics drivers and the Gnome Display Manager. Then, after some alterations...

```
sudo /etc/init.d/gdm start
```

to start the display manager, load the drivers and run the desktop again.

If you've managed to get your LTSP setup going you'll notice the login screen looks different to a normal desktop ubuntu install. This is because it is running LDM. LDM still runs the Gnome (or any other) desktop environment, but it is a different display manager to GDM.

I think LTSP needs this as it loads graphic drivers locally on the client, but logs in remotely to the server via secure shell.

Hope this all helps....

---

