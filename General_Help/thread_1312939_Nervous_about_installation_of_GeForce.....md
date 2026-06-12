---
title: "Nervous about installation of GeForce...."
date: 2009-11-03
forum: General Help
---

### Post by jhb1608 on 2009-11-03
I ordered this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133302](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133302)

And it's GeForce 210 512MB 64-bit DDR2 PCI Express 2.0 x16 HDCP Ready Video Card - Retail videocard.

I readed NVIDIA's linux driver website and I'm feeling nervous.

1) Should I put the videocard in first and install?

OR:

2) Pre-install and then install the videocard?

OR:

3) Should I put it, install it and upgrade?

I need to know before I do anything to my videocard.

---

### Post by jhb1608 on 2009-11-03
Well?

---

### Post by Onesimus on 2009-11-03
That must be some record 58 minutes waiting time before writing a further request !

Perhaps, your patience could match your nervousness.

---

### Post by jhb1608 on 2009-11-03
> **Onesimus said:**
> That must be some record 58 minutes waiting time before writing a further request !

Perhaps, your patience could match your nervousness.

Uhh... ok.

---

### Post by alphaniner on 2009-11-03
As Onesimus 'suggested', you really should wait longer than 1 hour before 'bumping' your post.

I installed an nVidia card into an existing installation using onboard nVidia graphics.  I didn't have any serious issues, but it's been a while so I don't remember exactly what I had to do.  I'm fair sure Ubuntu still booted to the GUI though.

I'd still advise a backup in case things go awry.

---

### Post by jhb1608 on 2009-11-03
> **alphaniner said:**
> As Onesimus 'suggested', you really should wait longer than 1 hour before 'bumping' your post.

I installed an nVidia card into an existing installation using onboard nVidia graphics.  I didn't have any serious issues, but it's been a while so I don't remember exactly what I had to do.  I'm fair sure Ubuntu still booted to the GUI though.

I'd still advise a backup in case things go awry.

Alright. Sorry for bumping.

---

### Post by alphaniner on 2009-11-03
Gah!  I think I didn't read your post carefully enough.  Just to be clear, there's no reason not to connect the card before installing fresh, if you are going to install anyway.  On the other hand, if you already have a working install, go ahead and connect the card and try to boot the existing install.

But again, you would be well served to backup important data.  The video card isn't likely to damage your data, but it could mess up the GUI, making it a hassle to retrieve your data if you're not comfortable with the terminal.

---

### Post by jhb1608 on 2009-11-03
Yrs, it is what I am saying. Thanks for your explaination. I don't mind the reinstallation if it messes me up. I uploaded my files in Ubuntu One so I'm ok. but I'll burn stuff in my CD anyways in case Ubuntu One get down.

---

### Post by frank_acies on 2009-11-03
I have the geforce 210 it seems to work just fine, save for the hdmi audio, I can't seem to get that working.

---

### Post by 3rdalbum on 2009-11-03
Put the card in and then install Ubuntu. In the Hardware Drivers program, choose to activate the Nvidia driver, then reboot. That's all there is to it.

---

### Post by jhb1608 on 2009-11-04
> **frank_acies said:**
> I have the geforce 210 it seems to work just fine, save for the hdmi audio, I can't seem to get that working.

I don't need audio, since I'm deaf, so I'm good. :).

---

### Post by jhb1608 on 2009-11-04
> **3rdalbum said:**
> Put the card in and then install Ubuntu. In the Hardware Drivers program, choose to activate the Nvidia driver, then reboot. That's all there is to it.

It is already installed, silly. So I have to do is put a videocard and boot Ubuntu and install the drivers, right? :).

---

### Post by ndefontenay on 2009-11-04
You can install the card first. Just do a backup of your xorg.conf. Worst case you can always modify it to use the default nvidia generic drive while you install and get your card's driver to work. Nothing big to be worried about.

---

### Post by jhb1608 on 2009-11-04
> **ndefontenay said:**
> You can install the card first. Just do a backup of your xorg.conf. Worst case you can always modify it to use the default nvidia generic drive while you install and get your card's driver to work. Nothing big to be worried about.

That's why I'm here and ask the question here. How do I backup the xorg.conf?

---

### Post by jhb1608 on 2009-11-04
How do I backup xorg.conf?

---

