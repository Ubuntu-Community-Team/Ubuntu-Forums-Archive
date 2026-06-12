---
title: "ATI 7970 and Ubuntu 11.10"
date: 2012-04-01
forum: General Help
---

### Post by Devilz_108 on 2012-04-01
Hello ;)
It was working great and I've been using Ubuntu for a long time but I've made an update to the graphics driver which made the Ubuntu un-useable which takes me to terminal when I login to Ubuntu no more regular Ubuntu

Any help please other than formatting and re-installing?

---

### Post by quadproc on 2012-04-01
Which driver were you successfully using before the update?

I will assume that you were using one of the ATI drivers; if not so then this reply will not apply to your situation.

You will need to uninstall the broken (updated) driver.  You should do this by using the uninstall script that came with the driver that you were using.  You should be able to do this from the command line.  Once that driver is gone, you will be running either the open source driver or one of the very simple drivers that comes with the system such as vesa.  That will be adequate to do an install of a driver that works; I suggest going back to the last driver that worked for you.

You might make some progress by renaming the /etc/X11/xorg.conf file to something like /etc/X11/xorg.conf-broken; the newer X windows versions will attempt to run without an xorg.conf file so renaming the file will effectively remove it and the X windows will try to do whatever makes sense with the hardware in your system.

My experience is that you should uninstall a driver before installing a new one.  If you don't then various bad things can happen from odd behavior of the system to a black screen.

Also, Ubuntu's Additional Drivers does not give you a choice of which version gets loaded so I suggest that you use ATI' s driver which you can download from their site.

quadproc

---

### Post by mavmic on 2012-04-01
are you offered a low graphics mode by your system at startup ?
did you have ATI drivers before the upgrade ?

---

### Post by Devilz_108 on 2012-04-02
No I didn't have any graphics driver when I've installed the ATI 7970 and what I get is only Terminal so I need commands to uninstall

---

### Post by CynicRus on 2012-04-02
m...You install ATI driver with .run file from official radeon site?

---

### Post by Devilz_108 on 2012-04-09
Nope the Ubuntu driver program

---

### Post by Devilz_108 on 2012-06-01
I'm not double posting but bumping the thread up instead of making a new one
Anyone got an idea to fix it without re-installing Ubuntu?
I'm sick of Windows 7 and crashes.

---

### Post by QIII on 2012-06-01
Last time I checked, the 7xxx series cards are not supported by the current Linux driver.  I'll see what up to date info I can find.

I think AMD/ATI riddled the pooch on this.

Edit:  looks like the driver is supposed to be ironed out, per Phoronix.  I'll do some more digging.

Also, see the link in my signature.  I don't use the additional drivers method because it has been problematic for me.

---

