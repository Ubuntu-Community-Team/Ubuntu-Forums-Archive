---
title: "External USB hardrive keeps getting read-only permission..."
date: 2011-02-17
forum: General Help
---

### Post by JCM_Pico on 2011-02-17
Hi there,
I have a computer with Ubuntu 10.04, with few disk space.
For downloading some torrents, I've connected a USB hardrive, ext4 formated. 
But this idea wasn't a solution, because the drive keeps getting read-only permission...
Is there any way of prevent this to happen?

---

### Post by TeoBigusGeekus on 2011-02-17
```
sudo chmod 777 /media/mountpointofdrive
```

---

### Post by JCM_Pico on 2011-02-18
Already try chmod 777 and it did not worked....
When I connect the usb device I have permission to write. After a few hours the system says its read-only...

Any more idea?

---

### Post by Lunes en Marte on 2012-06-19
> **JCM_Pico said:**
> 

Any more idea?

Hi there, I have an entirely simlar problem. 
I wonder if after almost one year of this post you found a solution for the problem. 

I use a Kingston SSD 128 GB, ext4, USB+eSATA, in both Ubuntu 10.04 in a Dell Latitude E4310 and Ubuntu 12.04 on a Dell Precision M4600, and in both laptops it becomes read-only after a few minutes, or hours, or days, apparently randomly. 

Thanks in advance.

---

### Post by nothingspecial on 2012-06-19
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Closed.

---

