---
title: "Remote Desktop in Ubuntu"
date: 2010-10-12
forum: General Help
---

### Post by altjx on 2010-10-12
I have a desktop with Ubuntu 10.10 along with a laptop with Ubuntu 10.10. I have configured Remote Desktop with the following settings on both machines. 
[IMG]http://img3.imageshack.us/img3/363/screenshotnwb.png[/IMG]

However, on either machine, I go to Terminal Server Client... I type in the IP address and I hit connect (with RDP selected) and I get this error

[IMG]http://img843.imageshack.us/img843/2535/screenshotto.png[/IMG]

Or using VNC
[IMG]http://img837.imageshack.us/img837/411/screenshotyrc.png[/IMG]

What am I doing wrong?

---

### Post by wavesailor on 2010-10-12
I not sure RDP works. You may have to use other VNC type programs.
Look for TightVNC or UltraVNC

---

### Post by altjx on 2010-10-12
> **wavesailor said:**
> I not sure RDP works. You may have to use other VNC type programs.
Look for TightVNC or UltraVNC

That's terrible, surprised it doesn't work since it came with the feature. Thanks. I'll go ahead and use VNC

---

### Post by pricetech on 2010-10-12
I always install xvnc4viewer to make Terminal Server Client work with VNC.

I use SSH between Linux machines though.  NX from nomachine dot com gives me a fully functional GUI.

---

### Post by altjx on 2010-10-12
> **pricetech said:**
> I always install xvnc4viewer to make Terminal Server Client work with VNC.

I use SSH between Linux machines though.  NX from nomachine dot com gives me a fully functional GUI.

I have xtightvncviewer installed on both machines as well but it still doesn't connect even using that. Basically it brings up TSClient but it has the "VNC" option available. How come that doesnt work either?

---

### Post by CharlesA on 2010-10-12
Also, you might have a problem connecting, since it's seeing the machine as "localhost."

What does ifconfig say?

---

### Post by altjx on 2010-10-12
> **CharlesA said:**
> Also, you might have a problem connecting, since it's seeing the machine as "localhost."

What does ifconfig say?

Ah, damn. I'll post it here when I get home.

---

### Post by gradinaruvasile on 2010-10-12
I use x11vnc as server - it supports ssh tunneling making it very secure.
And Remmina as client - it just blows the default terminal services client out of the water - has sftp file transfer support when connecting to ssh-tunneled vnc connections  - also it has real-time scaling, tabbed connections and whatnot.

---

### Post by altjx on 2010-10-12
> **gradinaruvasile said:**
> I use x11vnc as server - it supports ssh tunneling making it very secure.
And Remmina as client - it just blows the default terminal services client out of the water - has sftp file transfer support when connecting to ssh-tunneled vnc connections  - also it has real-time scaling, tabbed connections and whatnot.

Thanks for the info! Can't wait to get back home lol

---

### Post by bhoth on 2010-10-12
Uncheck the "Configure network automatically to accept connections" box, then goto Appearance Preferences, then select the Visual Effects tab and select "None".

Reboot the computer then it should work. It does on mine.

---

### Post by CharlesA on 2010-10-12
The only thing that "configure the network automatically" is use UPNP to open the ports on the router and let VNC open access to the internet.

That is not recommended since there are a slew of threads on this forum where a machine was compromised because VNC was allowed open access to the internet with a weak or no password.

---

### Post by mbgaski on 2010-10-12
> **altjx said:**
> That's terrible, surprised it doesn't work since it came with the feature. Thanks. I'll go ahead and use VNC

RDP (from a server standpoint) is a Windows-only technology.  As such, you really only use TSC to connect to Windows machines.  All Linux systems I've ever seen use VNC to implement remote usage (I think Macs do too).

Personally, I've never been a huge fan of VNC.  It works in a pinch, but using a remote X11 server tends to yield a more responsive setup IMHO.

---

### Post by pricetech on 2010-10-12
> **mbgaski said:**
> RDP (from a server standpoint) is a Windows-only technology.

True, but Terminal Server Client also makes a dandy VNC client once the proper VNC is added.

I gravitate towards it because I support so many windows boxen.

---

### Post by CharlesA on 2010-10-12
> **pricetech said:**
> True, but Terminal Server Client also makes a dandy VNC client once the proper VNC is added.

I gravitate towards it because I support so many windows boxen.

Has it always had that functionality? I've never noticed it before.

---

### Post by altjx on 2010-10-12
So wait... are all of these VNC solutions working just like TeamViewer? if so, might as well just use teamviewer... VNC stuff getting confusing.... and TV may be more easier to access locally and externally.

---

### Post by CharlesA on 2010-10-12
> **altjx said:**
> So wait... are all of these VNC solutions working just like TeamViewer? if so, might as well just use teamviewer... VNC stuff getting confusing.... and TV may be more easier to access locally and externally.

Correct.

---

