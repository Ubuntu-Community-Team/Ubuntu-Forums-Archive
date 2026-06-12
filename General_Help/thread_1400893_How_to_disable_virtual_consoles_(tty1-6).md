---
title: "How to disable virtual consoles (tty1-6?)"
date: 2010-02-07
forum: General Help
---

### Post by moxxite_jibun on 2010-02-07
Hi, so been looking for an answer to the following question, which is how do i successfully 
disable virtual consoles (tty1-6?) in karmic koala. Now i have six running and that is too much for 
me as a normal desktop user, 2 running is more what i'd like to use. I know how to do this in jaunty 
but as virtual console now longer exist on /etc/default file how can i disable the un-needed ones in karmic.

---

### Post by akashiraffee on 2010-02-07
> **moxxite_jibun said:**
> Hi, so been looking for an answer to the following question, which is how do i successfully 
disable virtual consoles (tty1-6?) in karmic koala. Now i have six running and that is too much for 
me as a normal desktop user, 2 running is more what i'd like to use. I know how to do this in jaunty 
but as virtual console now longer exist on /etc/default file how can i disable the un-needed ones in karmic.

Why would you bother?  Are they in your way or something?  

Just forget about them, they are not taking any resources away from your system.   The most harm they could be doing is (apparently) forming some kind of irrational distraction for your muddled mind (no offence).  Stop wasting your time thinking about this, there are plenty of meaningful things more deserving of your attention and concern.

---

### Post by NCLI on 2010-02-07
I agree with Akirashiraffee. There's absolutely no reason to disable them, why would you?? :confused:

---

### Post by warp99 on 2010-02-07
Backup the file /etc/securetty, then remove or comment out the terminals you wish not to login.

Edit: Sorry that's just if you want to restrict root logins to those terminals. If you want to disable the terminals just move or remove the upstart files in /etc/init:

```
/etc/init$ ls tty* -1
tty1.conf
tty2.conf
tty3.conf
tty4.conf
tty5.conf
tty6.conf
```

---

### Post by moxxite_jibun on 2010-02-07
For Akashiraffee: 
No problem there. and yes there is lot more important things to do when talking about tuning up the system,
In case if there's no real noticeable advantage of disabling them? i just might then leave them alone as they are.

For NCLI: 
Way back when i was using jaunty
many people did recommend to disable the unneeded virtual consoles. And from there this question lingered to my mind.

For warp99:
thank you for help. but this /etc/init: method does not seem to work for me. 
The file is empty when i open it, as i think this is because in karmic tty no longer resides in that place. (not sure) 
and why it aint there is probably because of grub2 as far as i undestand something. And yes i want/wanted to disable the terminals not remove them from the system :P

---

### Post by warp99 on 2010-02-07
> **moxxite_jibun said:**
>  And yes i want/wanted to disable the terminals not remove them from the system :P

The terminals are disabled since they're never generated, but if you do use ctrl-alt-f* you end up switching to a blank screen. Before upstart you would edit the /etc/inittab file to disable the terminals, but since upstart this is the only method AFAIK. The other would be to rebuild the XF86 source, but I hardly think you would want to do that. ;)

---

### Post by moxxite_jibun on 2010-02-07
> **warp99 said:**
>  but since upstart this is the only method AFAIK. The other would be to rebuild the XF86 source, but I hardly think you would want to do that. ;)
Oh! now i actually grasped and did comprehend something of how it works cheers! 
And yes you got it absolutely right mate, just...not ready yet for for rebuilding the source maybe someday then and that is   "when i have more trust in me" :biggrin:

---

### Post by allxk on 2010-02-08
Every reboot it gets 2 minutes delay on tty1 user login:
then continue to GUI Gnome.
Thats why this should be disabled some how.
please help!!

---

### Post by dcstar on 2010-02-08
> **allxk said:**
> Every reboot it gets 2 minutes delay on tty1 user login:
then continue to GUI Gnome.
Thats why this should be disabled some how.
please help!!

Absolute rubbish, any delay is another process taking time to run and has absolutely nothing to do with the TTYs which are just waiting their turn to be enabled.

---

