---
title: "Separate Evolution user file"
date: 2011-05-04
forum: General Help
---

### Post by Greg1953 on 2011-05-04
I use U.10.4.
I have to take over the work of another, but all I have is the Hard Drive from that machine.
Because the two positions are separate, I do not want to Import his Evolution over my own - but, I do want to be able to access it from my machine.
Can my Evolution refer to the old hard drive (now in a caddy and non-bootable) for the Evolution account data that is there, while still being able to switch back to my own Evolution data on demand.
E.G. in Windows the equivalent would be the way that Outlook can refer to different .pst files at loading.
Alternatively, can I make the external USB drive (previously a running main HDD) bootable without losing all of the data?

---

### Post by dcstar on 2011-05-04
> **Greg1953 said:**
> I use U.10.4.
I have to take over the work of another, but all I have is the Hard Drive from that machine.
Because the two positions are separate, I do not want to Import his Evolution over my own - but, I do want to be able to access it from my machine.
Can my Evolution refer to the old hard drive (now in a caddy and non-bootable) for the Evolution account data that is there, while still being able to switch back to my own Evolution data on demand.
E.G. in Windows the equivalent would be the way that Outlook can refer to different .pst files at loading.
Alternatively, can I make the external USB drive (previously a running main HDD) bootable without losing all of the data?

Evolution files must be on a Linux partition - NOT a Windows one - and you can make a link to the new location to replace the existing .evolution folder in your /home.

Just get the permissions correct.

---

### Post by Greg1953 on 2011-05-04
Thanks, David.
Both drives are Ubuntu 10.4.
Does your solution mean that I would have to physically replace the .evolution folder each time that I needed to access the mail there?

I was hoping for a solution that would allow me to point to the other drive (even as a mapped drive) so that swapping back and forth would be just like logging in and out, rather than like destroying and replacing the folders.

What would be the result of my creating another login identity on my laptop? Does Ubuntu 10.4 support multiple users each with a separate Evolution folder?

---

### Post by Greg1953 on 2011-05-05
Thanks - just for being here.

In formulating my questions and passing on info. I have answered my own questions sufficiently for me to mark this one solved now.

I don't have the solution that I was looking for exactly, but, I do have access to the OTHER Evolution file, simply by creating a second identity on my laptop and importing the backup of that file into there.

Seems simple, right? Obvious even? Only after you've had the experience.
Greg.

---

