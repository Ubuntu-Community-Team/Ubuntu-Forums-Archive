---
title: "Ubuntu as a NAS"
date: 2012-04-08
forum: General Help
---

### Post by minigilani on 2012-04-08
Hi

I'm helping someone that needs an efficient way for their small business to store huge amounts of data. Obviously, i recommended using an old box, set up with a headless Ubuntu Server and loads of hard disks attached to it. I'm a fairly educated noob; comfortable with the command line and know my way around ssh but i don't really know much about NAS.

Could anyone tell me a list of packages or point me in the right direction on this? One requirement is that the box **must have user management**. Like only allowing users to access their own assigned folders. I have no idea how this works, any help or pointing me to a tutorial would be appreciated.

Also, if someone would be kind enough to help me find a tutorial on RAID, it would make them just that much more awesome! 

Cheers!

---

### Post by ridetheteapot on 2012-04-08
Honestly just checkout freenas. It has zfs, the king of filesystems.
Also is already setup for usage as nas, with a really nice web ui.

---

### Post by Cheesemill on 2012-04-08
> **ridetheteapot said:**
> Honestly just checkout freenas. It has zfs, the king of filesystems.
Also is already setup for usage as nas, with a really nice web ui.

+1

If your machine is only going to be used as a NAS and nothing else then you can have FreeNAS installed and set up in minutes.

---

### Post by minigilani on 2012-04-08
Yup, i'm pretty sure we'll only use it as a NAS. Is it stupid proof? because i have no experience with FreeBSD.

---

### Post by Cheesemill on 2012-04-08
> **minigilani said:**
> Yup, i'm pretty sure we'll only use it as a NAS. Is it stupid proof? because i have no experience with FreeBSD.
Yep, pretty much. All configuration is done using a web interface, no command line action needed.

You could always try it out in a VM first to see what it's like.

Documentation:
[http://www.freenas.org/images/resources/freenas8.0.3/freenas8.0.3_guide.html](http://www.freenas.org/images/resources/freenas8.0.3/freenas8.0.3_guide.html)

Downloads are own the home page:
[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by minigilani on 2012-04-08
> **Cheesemill said:**
> Yep, pretty much. All configuration is done using a web interface, no command line action needed.

You could always try it out in a VM first to see what it's like.

Awesome, thanks! Marking the thread solved.

---

