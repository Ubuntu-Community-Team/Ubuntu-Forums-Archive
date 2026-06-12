---
title: "Strange Samba Problem"
date: 2009-07-21
forum: General Help
---

### Post by zzzBrett on 2009-07-21
I have a samba server setup, and am tryin to access it from a vista computer.

When I access it via the IP address (\\192.168.x.x), it works fine.  But when I access it via the computer name (\\server), I can see all of the shares available, but when I double click one and type in the username / password, it says access denied.

Any ideas why this may be happening?

---

### Post by jeromedavies on 2009-07-21
I've had a similar problem with accessing samba shares from windows. It was related to name resolution and network / internet security settings on windows. If I remember more I'll post again. 

Have you tried putting the name of your samba server into your vista hosts file

[http://geekswithblogs.net/thibbard/archive/2006/12/13/ChangingYourHostsFileInVista.aspx](http://geekswithblogs.net/thibbard/archive/2006/12/13/ChangingYourHostsFileInVista.aspx)



[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

---

### Post by zzzBrett on 2009-07-21
> **jeromedavies said:**
> I've had a similar problem with accessing samba shares from windows. It was related to name resolution and network / internet security settings on windows. If I remember more I'll post again. 

Have you tried putting the name of your samba server into your vista hosts file

[http://geekswithblogs.net/thibbard/archive/2006/12/13/ChangingYourHostsFileInVista.aspx](http://geekswithblogs.net/thibbard/archive/2006/12/13/ChangingYourHostsFileInVista.aspx)



[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)


Yes, the name is in the hosts file.

I'm not sure why, but I had to do that in order for my windows computers to use the netbios name, but with linux computers, I didn't have that problem (didn't have to use the Hosts file) -- not sure if that is at all related..

---

### Post by bacardiandwatermelon on 2009-07-21
Don't know if there is a fix or not, but in Jaunty if I setup a samba share using a right click from nautilus, windows machines couldn't access the share. But if I removed that share and setup a new one using the /etc/smb.conf then the share worked fine. Maybe give this a try if you haven't already...

---

### Post by jeromedavies on 2009-07-22
I found these two links that may help. The first actually  points to the second and suggests the WINS name resolution.

[http://forums.techarena.in/windows-vista-network/670498.htm](http://forums.techarena.in/windows-vista-network/670498.htm)

[http://opensuse.swerdna.org/susesambabrowse.html](http://opensuse.swerdna.org/susesambabrowse.html)

---

