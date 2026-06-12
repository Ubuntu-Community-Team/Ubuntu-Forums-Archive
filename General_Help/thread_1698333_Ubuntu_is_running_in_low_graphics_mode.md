---
title: "Ubuntu is running in low graphics mode"
date: 2011-03-02
forum: General Help
---

### Post by Cheryl J. Jones on 2011-03-02
Hi,
I have Ubuntu 10.10 and when I boot my PC I can see the following message: Ubuntu is running in low graphics mode and Ubuntu stops booting. I can-t boot in it I can only use command line.
I think I accidentally uninstalled some packages clicking at completely removal at some ipod utilities in synaptic. How can I fix this?
Your help is sincerely appreciated

Cheers

---

### Post by fabricator4 on 2011-03-02
What graphics card do you have?  If you don't know you might be able to find out by typing 'lspci' on the command line.  You're looking for some lines that start with "VGA controller" and/or "Display Controller"

Also, if you boot into recovery mode do you get a low resolution GUI at all?

---

### Post by grahammechanical on 2011-03-02
I started to get this. It was due to my graphic/video card overheating (it was a fanless type) and failing to pass the monitor resolution settings onto the X-Server.

I am sorry to give you the bad news that you might need to buy a new video card. I had to.

Regards.

---

### Post by fabricator4 on 2011-03-02
> **grahammechanical said:**
> I started to get this. It was due to my graphic/video card overheating (it was a fanless type) and failing to pass the monitor resolution settings onto the X-Server.

I am sorry to give you the bad news that you might need to buy a new video card. I had to.

Regards.

You can get around this by passing the monitor sync specifications in xorg.conf

I still have to do this for one of my machines because it is running though a KVM switch.  The switch does not pass the frequency parameters even if the monitor is switched to the Ubuntu machine at boot time.

Chris

---

