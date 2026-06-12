---
title: "Hulu Desktop"
date: 2009-12-28
forum: General Help
---

### Post by wookietim on 2009-12-28
Just installed Hulu desktop and it works really well under Ubuntu. And using my laptops HDMI output I can toss it on my TV... My question - is there any remote control I can use with Ubuntu to control it? Preferably, an app I can install on my Android phone...

---

### Post by zkriesse on 2009-12-28
Doubt it but doesn't hurt to check so I'd give it a peek. :)

---

### Post by laceration on 2009-12-28
I doubt that there is an Android app that would make it work as a remote control w/ Linux.  What would it use, Blootuth?  From what I've seen Linux is not that flexible in getting inputs + driving it as a remote.

A standard Microsoft Media Center remote with an usb receiver and LIRC will work with Hulu Desktop.  I have done it.  One of these remotes can be had for not much more than $20.

Hulu Desktop is probably the best app for watching web TV, but still sucks in comparison to regular old tv.  It's interface is laggy, there is too much content to navigate through, the video often stops while buffering and looks jerky with its low framerate.  And I have decent hardware and fast broadband.

So I never use Hulu Desktop, but have a dvb card and watch over the air and unecrypted cable in vastly superior High Definition on my computer and skip right through commercials.

---

### Post by wookietim on 2009-12-28
You don't happen to have any specific remotes you could suggest do you? I don't feel like buying one and then finding out Linux doesn't recognize it...

---

### Post by laceration on 2009-12-28
> **wookietim said:**
> You don't happen to have any specific remotes you could suggest do you? I don't feel like buying one and then finding out Linux doesn't recognize it...

You are smart. I have gone through that nightmare.  Best strategy is to find one, because there are not a ton of them out there, and see if it is reported to work in Linux in customer reviews.

I did that in about 1 minute:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001&cm_re=remote_control_media_center-_-80-121-001-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121001&cm_re=remote_control_media_center-_-80-121-001-_-Product)

---

### Post by wookietim on 2009-12-28
Thanks dude! I'm not a hardware person (I do my stuff on the software side) so when it comes to finding hardware that is compatible with Linux I have a track record of failing pretty badly when I do it on my own...

---

### Post by strc on 2010-01-10
There's a free-as-in-beer app for android called gmote, which lets you use your phone as a remote.  It works over TCP, either through wifi or your phone's data connection.  There's a closed-source linux server you can download for it, but it looks like it only supports VLC as a media player.  I prefer MPlayer to VLC, so I haven't bothered to try this myself..

...  Heh, now that I look around the android marketplace, I see that there's an app that does exactly what you're looking for.  [http://remotedroid.net](http://remotedroid.net) - it works perfectly for me on Karmic, as a generic mouse and keyboard under X.  The only dep is having a java runtime

---

### Post by wookietim on 2010-01-11
I tried that... the server app runs, the Android app runs... and they don't talk to each other. I keep hoping that maybe one version or another will work, but they don't quite connect yet...

---

### Post by Cadeyrn on 2010-05-03
> **laceration said:**
> Hulu Desktop is probably the best app for watching web TV, but still sucks in comparison to regular old tv.  It's interface is laggy, there is too much content to navigate through, the video often stops while buffering and looks jerky with its low framerate.  And I have decent hardware and fast broadband.

I'm not a fan of the HuluDesktop menus/navigation and how f***ing long it takes to get to your show, but other than that the stuff you listed here happens to me on the Hulu website but NOT on HuluDesktop... Pretty funny to me.

---

### Post by plus2plus on 2010-05-03
> My question - is there any remote control I can use with Ubuntu to control it?
[Hulu Desktop]("http://www.hulu.com/labs/hulu-desktop-linux") for Linux supports input from hundreds of infrared remote controls using the LIRC open source package. You can download LIRC and receive general configuration information from [http://www.lirc.org](http://www.lirc.org), as well as browse a list of supported remote controls. Hulu Desktop for Linux requires that lircd be run with the -r (--release) switch.

You can also configure Hulu Desktop's LIRC hardware interface, key mappings, and more by modifying the remote section of ~/.huludesktop. For more information, refer to /usr/share/doc/huludesktop/README.

---

