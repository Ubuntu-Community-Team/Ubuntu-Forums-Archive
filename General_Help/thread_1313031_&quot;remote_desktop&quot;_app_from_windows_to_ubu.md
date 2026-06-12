---
title: "&quot;remote desktop&quot; app from windows to ubuntu??"
date: 2009-11-03
forum: General Help
---

### Post by tlyczko on 2009-11-03
I'm setting up an Xubuntu VM that people can use for secure browsing.

What is a Windows application they can use to remotely access this VM in a manner equivalent to Windows' Remote Desktop, please??

Thank you, Tom

---

### Post by dchurch24 on 2009-11-03
You could try VNC: [http://www.tightvnc.com/download.php](http://www.tightvnc.com/download.php)

You would have to run the server edition in the VM and it would have to be running for clients to be able to connect.

You would also have to have routing sorted out to send the port to the right machine. I use this across continents and although it's a little slow (understandably), it's perfectly usable.

---

### Post by tlyczko on 2009-11-03
This will all be within two subnets in the same Windows domain.

I later found FreeNX which people say is faster and relatively more secure.

Thank you, Tom

---

