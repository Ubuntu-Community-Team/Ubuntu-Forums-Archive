---
title: "Firefox 4 64bit flash"
date: 2011-03-08
forum: General Help
---

### Post by bill2507733 on 2011-03-08
hi everyone. 

i just switched to Ubuntu and have run into my first problem. I am running 64 bit 10.10 and firefox 4 b12. i can not get flash to work! plz help

---

### Post by howefield on 2011-03-08
What have you tried ?

You could run 32 bit flash by installing flashplugin-installer via Synaptic Package Manager, or download the "Square" preview release of 64 bit flash from Adobe and copy it to /usr/lib/mozilla/plugins

Alternatively, you might also be able to use a firefox addon called Flash-Aid which will install the appropriate flash for you, but I am not sure if it is ready to go with the version of Firefox that you are running.

---

### Post by bill2507733 on 2011-03-08
tried all posible flash downloads.

where do i place the square one?

---

### Post by howefield on 2011-03-08
> **bill2507733 said:**
> where do i place the square one?

As above...

```
/usr/lib/mozilla/plugins
```

---

### Post by bill2507733 on 2011-03-08
ive already placed it there and it does not work 


should i just reinstall 32 bit ubuntu?

---

### Post by howefield on 2011-03-08
> **bill2507733 said:**
> should i just reinstall 32 bit ubuntu?

That's your choice, but it sounds a sledgehammer to crack a nut.

I've checked the Flash-Aid addon, it seems to be available for Firefox 4 b12. I'd try that before installing the operating system again.

Flash-Aid will remove all conflicting versions of flash and install one which works.

---

### Post by bill2507733 on 2011-03-08
tried flash aid 

seemed like it worked but still no

---

### Post by howefield on 2011-03-08
You did restart the browser after installing ?

Is it all flash sites that you can't get to work, or is it some specific one ?

Sorry, not much more I can suggest.

---

### Post by bill2507733 on 2011-03-08
this is really frustrating me. 


I have tried everything includin full restart

---

### Post by Zdk on 2011-03-10
Try this - open a terminal and run these commands:


Gets most recent version of the "Square" flash player.
```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz
```First command extracts the player, the others create symbolic links to  the file in the other directories in case they require it. I am using  FF4b13 and did not have to do this, but you might, and I can't see a  reason not to.
```
sudo tar xfv flashplayer10_2_p3_64bit_linux_111710.tar.gz -C /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-4.0-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
```Deletes the tar.
```
sudo rm -rf flashplayer10_2_p3_64bit_linux_111710.tar.gz
```Hope this helps![INDENT]-Zack
[/INDENT]

---

### Post by Vaphell on 2011-03-10
OP, what does your firefox say in about:****plugins page (type that in address bar)? what version of flash it shows if any?

---

### Post by KleeWho on 2011-03-24
I copied square to /usr/lib/firefox-4.0/plugins/ and it works. I'm using stable ff from mozilla ppa

---

### Post by ironjaw33 on 2011-03-29
> **KleeWho said:**
> I copied square to /usr/lib/firefox-4.0/plugins/ and it works. I'm using stable ff from mozilla ppa

This worked for me as well for the 4.0 release.

---

### Post by pwabrahams on 2011-04-02
In order to get 64-bit Flash to work with Firefox 4.0, I had to copy the file **libflashplayer.so** from **/usr/lib/flashplugin-installer** to**/usr/lib/mozilla/plugins/**.

---

### Post by revfycd on 2011-06-15
> **howefield said:**
> What have you tried ?

You could run 32 bit flash by installing flashplugin-installer via Synaptic Package Manager, or download the "Square" preview release of 64 bit flash from Adobe and copy it to /usr/lib/mozilla/plugins

Alternatively, you might also be able to use a firefox addon called Flash-Aid which will install the appropriate flash for you, but I am not sure if it is ready to go with the version of Firefox that you are running.

Thanks for your help. my flash used to work on chrome. now it works on firefox ,thank you.

---

