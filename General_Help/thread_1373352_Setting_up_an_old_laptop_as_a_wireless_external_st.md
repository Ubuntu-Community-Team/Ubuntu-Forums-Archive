---
title: "Setting up an old laptop as a wireless external storage device"
date: 2010-01-05
forum: General Help
---

### Post by imposter on 2010-01-05
I'm looking for some general advice on how to best setup an old laptop as an external storage device.  I have an external usb drive that I want to plug into it and setup my laptop to connect to it and use it to store random files.  The old laptop is running Ubuntu 9.1/XP dual boot.  My new laptop is Ubuntu 9.1/Windows 7.  My wife's laptop, which I'd also like to be able to connect to the old laptop wirelessly, is only Windows 7.  

What's the best way to setup the old laptop so my new laptops can connect to it?

---

### Post by pricetech on 2010-01-05
I'm assuming your network connection is working so we'll start with Samba.  Install from the repos and configure using System - Administration - Samba (That's where it is under Hardy).

You can share stuff read only or read write.  You can share it with everybody or only specific users, but the users will have to exist on the "server" laptop before they will be listed as users in the Samba configuration applet.

Choose your shares based upon whatever your need is.

After that just restart Samba and everything should work.

---

### Post by llamabr on 2010-01-05
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)

I find samba to be overkill for something like this.

---

### Post by RedSingularity on 2010-01-05
+ 1 for the samba server.  And you can use webmin to administer the server.  The samba server allows windows machines to access the files as well.

---

### Post by imposter on 2010-01-05
I believe I have samba running correctly on the server laptop. I can connect to it from my new laptop by going to Places->connect to server, and putting in the ip address.  I get a list of directories.  But when I try and open the directory, I get an error message - unable top open windows share.  This is coming from the external drive that is connected to the server laptop.  If I try and connect to a directory internal to the server laptop, it seems to work fine.  Any ideas why the external drive won't mount?

As to NFS - I'm not sure if that'd work well for windows, but I'm willing to give it a go if samba doesn't work out.

---

### Post by pricetech on 2010-01-08
Just a wild guess;  Ownership of the external drive could be an issue.  Check that and make sure you are explicitly sharing it through Samba.

---

