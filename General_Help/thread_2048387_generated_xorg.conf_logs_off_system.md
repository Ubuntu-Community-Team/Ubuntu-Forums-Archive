---
title: "generated xorg.conf logs off system"
date: 2012-08-26
forum: General Help
---

### Post by firekage on 2012-08-26
Hi.

I would like to ask for Your help. 

Since my first installation of Ubuntu i've had problems with running Ubuntu on newer graphic driver than those installed/shipped with Ubuntu. 

For an example, with Ubuntu 12.04 everything works perfect with his own nvidia-drivers 295.xx but as soon as i install something new, new drivers like 304.37 from x-swat ppa,  than i have problems with Ubuntu such as problems with xorg/drivers/screen realted issues.

 I will try to explain it a little more. My problem is realted to logging off Ubuntu when, for an example, i use, i run smplayer but only when xorg.conf is generater either trough nvidia control panel and saving to x (by gui) or when generated trough terminal by running nvidia-settings.

When there is no xorg in ubuntu, everything works but sometimes i have problem with twinview, which i doesen't need, doesen't use because i have only on LCD screen. TwinView sometimes turn itself without choosing it to run. 

If i generate xorg.conf in order to disable TwinView by adding few lines to xorg.conf then i have problems with auto logging off Ubuntu, as i mentioned above when, for an example, i use smplayer (i saw this even when i once used ktorrent).

As a matter of fact, i don't know what to do in order to have twinview disabled, in order to never run again and in order to have xorg.generated but without the issue with logging off ubuntu when i use something (it happened once even when i used something from unity launcher).

Can You help me? I will add also few screens that shows why TwinView bugs me, remember - i have only one screen but sometimes it looks like this:

1:
[http://img404.imageshack.us/img404/4092/1screennvidia304371204.png](http://img404.imageshack.us/img404/4092/1screennvidia304371204.png)

2:
[http://img404.imageshack.us/img404/4092/1screennvidia304371204.png](http://img404.imageshack.us/img404/4092/1screennvidia304371204.png)

3:
[http://img404.imageshack.us/img404/2235/twinviewenabledbyitself.png](http://img404.imageshack.us/img404/2235/twinviewenabledbyitself.png)

**Screen number 1** shows how it should be. **Screen number 2** shows that sometimes Ubuntu detects 3 screens, that's no true at all. **Screen number 3** shows what happens with my screen when twinview enabled itself - for an example, i use hibernation, i use suspend, i choose another output in my LCD screen when i have something connected to it (there shouldn't be any interferences between this because my computer is connected to DVI, to VGA i have connected different computer and i only change output in LCD menu).

---

### Post by dino99 on 2012-08-26
Latest nvidia driver does not work at all with actual xserver-xorg-core (ABI issue).

So either use the genuine driver or use nouveau till nvidia fix that issue.

---

### Post by firekage on 2012-08-26
> **dino99 said:**
> Latest nvidia driver does not work at all with actual xserver-xorg-core (ABI issue).

So either use the genuine driver or use nouveau till nvidia fix that issue.

Could you write more about it? What is ABI issue? Can i install xserver-xorg-core that would not have problems with ABI? As a matter of fact it works, just sometimes twinview enables itself.

BTW - my problem is not related to the latest nvidia driver but with all drivers exept 295.40 from Ubuntu repos. All from nVidia site, all from x-swat do the same. There is problem with all of them.

As i said - without xorg.conf it works, with xorg.conf as soon as i launch someting from unity launcher, launch smplayer then my system logs off. Only when there is xorg.conf file generated in /etc/X11/

---

### Post by firekage on 2012-08-30
Em i really the One with this problem?

---

