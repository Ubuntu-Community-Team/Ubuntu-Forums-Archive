---
title: "Remote Desktop"
date: 2009-09-29
forum: General Help
---

### Post by prem1er on 2009-09-29
Does anyone have any suggestions on a remote desktop solution for a headless server.  I've been all over google and can't find one decent howto on getting it set up and configured correctly. I'm running Ubuntu Server 9.04.  Any suggestions with links would be appreciated.

---

### Post by wojox on 2009-09-29
You're server doesn't have a gui does it?

---

### Post by the_squircle on 2009-09-29
> **prem1er said:**
> Does anyone have any suggestions on a remote desktop solution for a headless server.  I've been all over google and can't find one decent howto on getting it set up and configured correctly. I'm running Ubuntu Server 9.04.  Any suggestions with links would be appreciated.
I use NoMachine's NX for my headless server and it works flawlessly. It's three simple packages to install, one after the other, and it uses SSH to encrypt and secure the traffic. There is no configuration or anything.
[Here,](http://www.nomachine.com/download-package.php?Prod_Id=1169) you must download the client, node, and server. Just 'sudo dpkg -i nxclient.x.y.z.deb', then the node and the server.

Cheers!

---

### Post by prem1er on 2009-09-29
> **wojox said:**
> You're server doesn't have a gui does it?

No.

---

### Post by prem1er on 2009-09-29
> **the_squircle said:**
> I use NoMachine's NX for my headless server and it works flawlessly. It's three simple packages to install, one after the other, and it uses SSH to encrypt and secure the traffic. There is no configuration or anything.
[Here,](http://www.nomachine.com/download-package.php?Prod_Id=1169) you must download the client, node, and server. Just 'sudo dpkg -i nxclient.x.y.z.deb', then the node and the server.

Cheers!

Thanks, I'm looking into this now.

---

### Post by wojox on 2009-09-29
Just go to Places > Connect to Server > Service type: ssh 

Fill in the rest.

---

### Post by prem1er on 2009-09-29
> **wojox said:**
> Just go to Places > Connect to Server > Service type: ssh 

Fill in the rest.

I'm not sure what you mean. You want me to do this on my client machine?

---

### Post by the_squircle on 2009-09-29
> **wojox said:**
> Just go to Places > Connect to Server > Service type: ssh 

Fill in the rest.

I think what (s)he is looking for is a graphical remote access solution, like VNC or NX.

---

### Post by wojox on 2009-09-29
If your running Ubuntu, yes.

---

### Post by prem1er on 2009-09-29
> **wojox said:**
> If your running Ubuntu, yes.

Might not be running Ubuntu on the client machine. I am looking for a graphical solution to work with both linux and windows as the client.

---

### Post by wojox on 2009-09-29
Gotcha :P

---

### Post by the_squircle on 2009-09-29
> **prem1er said:**
> Might not be running Ubuntu on the client machine. I am looking for a graphical solution to work with both linux and windows as the client.

Then my NX solution is your best bet. It has numerous improvements over VNC, and it's secure and fast. You can just download the NX client for Windows from [nomachine.com](http://nomachine.com).

---

### Post by i.r.id10t on 2009-09-29
On a lan or over the 'net?  On a LAN, just enable XDMCP and connect with a X server on your local machine (X11 in Linux/Mac or cygwin-x in Windows).

Over the 'net, you can tunnel single applications over ssh (again, X11 on Linux/Mac or cygwin-x on win32).  Or you can set up VNC with SSH, which is a pain.

---

### Post by prem1er on 2009-09-29
Thank you both.

---

### Post by prem1er on 2009-09-29
> **i.r.id10t said:**
> On a lan or over the 'net?  On a LAN, just enable XDMCP and connect with a X server on your local machine (X11 in Linux/Mac or cygwin-x in Windows).

Over the 'net, you can tunnel single applications over ssh (again, X11 on Linux/Mac or cygwin-x on win32).  Or you can set up VNC with SSH, which is a pain.

I'm looking for a solution that will work outside of my LAN.

---

### Post by the_squircle on 2009-09-29
> **i.r.id10t said:**
> On a lan or over the 'net?  On a LAN, just enable XDMCP and connect with a X server on your local machine (X11 in Linux/Mac or cygwin-x in Windows).

That's basically what NX does; it tunnels the X connection over SSH, but in an easy-to-use way.

---

