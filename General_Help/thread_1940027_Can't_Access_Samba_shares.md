---
title: "Can't Access Samba shares"
date: 2012-03-12
forum: General Help
---

### Post by josiahrulez on 2012-03-12
So a few days ago my flatmates told me that they were unable to access the shares on my Download box (Ubuntu 11.04). Then this morning i woke up and was unable to access any shares either.

I can still remote in with Teamveiwer & VNC, and i can also access the SABnzbd & Sickbeard webpages (Running on my download box)

So none of my computers can access the samba shares, but i can access them from the computer itself by typing *smb://turtlesvr/*


What I've tried so far
[LIST]
[*]I downloaded and applied updates to linux 11.04 and restarted
[/LIST][LIST]
[*]I've tried using its hostname & IP but neither works.
[/LIST]
[LIST]
[*]I've tried putting the port numbers 137, 138, 139, 445 (Apparently samba uses these ports?) into the firewall, but this didn't work either.
[/LIST]

---

### Post by Habitual on 2012-03-13
Can you shell into the host and run ```
testparm -s
```?
Sanitize the output and post.

thanks.

---

