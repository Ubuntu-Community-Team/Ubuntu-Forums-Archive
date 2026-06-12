---
title: "Making sure network drives log out."
date: 2011-05-10
forum: General Help
---

### Post by Xeneth on 2011-05-10
Mu server at home has ssh running, and I mound it on my laptop through sftp in the GUI.  I came a cross a problem yesterday that I would rarely come accross, but I do want to make sure it's not an issue.

I mounted while over a friends house and worked great, but when I left, I just shut down my computer.  After that, I could not mount it again for a period because it was being secure thinking it was a "man in the middle attack".

What I want to know is if I unmount the drive though GUI (natty in classic mode), will that log me out of the SSH connection.

Second question is what would I edit, and what do I add to get this to be done automatically, rather sleep, hibernate, or shutdown (more interested in shutdown)?

---

### Post by Xeneth on 2011-05-11
?  no-one knows?  

How about this, is there a way to ID the laptop, no mater the location, so that way this issue does not arise again?

---

### Post by Xeneth on 2011-06-02
I found out why it was happening.  My server doesn't like me using the external IP address while on the same network as it is.  Works good if I use public IP outside, and private inside.  Did not like me using public IP from inside my network.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **canzeber said:**
> 

That's just a tad bit off topic, don't ya think?

---

### Post by Xeneth on 2012-01-12
Issue was that I was trying to use the public IP to connect to the server while I was on my internal network.

---

