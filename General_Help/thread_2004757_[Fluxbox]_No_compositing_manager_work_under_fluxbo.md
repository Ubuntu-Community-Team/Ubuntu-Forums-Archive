---
title: "[Fluxbox] No compositing manager work under fluxbox [12.04]"
date: 2012-06-16
forum: General Help
---

### Post by spupy on 2012-06-16
Cairo-compmgr has never worked properly on of my computers. Xcompmgr/compton used to work flawlessly with Arch and the previous Ubuntu version; not anymore. When I start xcompmgr, it gives no errors, but nothing visible happens. The command I'm using is supposed to give nice shadows.  

I installed the proprietary Nvidia drivers. Not sure with which drivers (OSS or proprietary) does Ubuntu come at installation, but it didn't work with them either.

So, is anyone using any compositing managers under fluxbox? I haven't actually tried Compton, because I can't find a deb file, and I'm kinda lazy at the moment to compile from source.

I prefer to have shadows, since they work better than thick window borders on my netbook's screen. Xcompmgr is also much more light-weight (sp?) than other window managers/desktop environments. (I haven't tried XFCE4, but I doubt it's as configurable as fluxbox.)

Thanks for any help or tips!

---

### Post by flemur13013 on 2012-06-16
FWIW, I use fluxbox and (brief test) xcompmgr didn't do anything except remove the window titlebars and mess up the mouse. Tho maybe I didn't start it correctly; the man page is no help.

> (I haven't tried XFCE4, but I doubt it's as configurable as fluxbox.)


Xfce4 is a real PITA compared to fluxbox.

---

### Post by spupy on 2012-06-16
> **flemur13013 said:**
> Tho maybe I didn't start it correctly; the man page is no help.

If I recall correctly, it should display some basic shadows even if you supplied no parameters. But otherwise I see the same thing that happens to you.

---

### Post by spupy on 2012-06-17
Installed Compton from source, it works. Maybe Xcompmgr is just too old now to work on newer distributions.

---

### Post by mrfreen on 2012-06-24
Ok, for those like me who were a little lost, Compton can be found here:
[https://github.com/chjj/compton](https://github.com/chjj/compton)

Just download the source zip (think is up the top of the page)
unpack it somewhere suitable (like ~/src)
then in a console navigate to the source directory and type
> make
sudo make install

---

### Post by flemur13013 on 2012-06-24
Compton seems to work. 

I had to install:
 - libxcomposite-dev
 - libxdamage-dev
 - libxrender-dev
to make it.

Note that the website and the README file have outdated documentation; use
$ compton --help
instead.

Edit:  To get mild shadows to the left and down:

$ compton -c -r 5 -l -12 -t -5 -o .5

The "l" and "t" (left and top shadow offsets) parameters are flakey.

---

### Post by spupy on 2012-06-25
> **flemur13013 said:**
> Edit:  To get mild shadows to the left and down:

$ compton -c -r 5 -l -12 -t -5 -o .5

The "l" and "t" (left and top shadow offsets) parameters are flakey.

The one I use:

```
compton -c -t-10 -l-14 -r10 -o1 &
```

---

### Post by Rick.B9 on 2012-06-28
Interesting thread!  I've been getting ready to update from my trusty 10.04 install to 12.04, and I hadn't thought about xcompmgr not working after the upgrade.  I only use it with terminal, so I start it only when I need it.  Transset and xcompmgr were all I needed to install at the time; I see things have moved on, as usual.

---

### Post by loukingjr on 2012-07-10
I'm not sure if anyone can help with this or not. I installed Fluxbox in my Lubuntu 12.04 install. Since the shadows in xcompmgr broke I installed Compton. Everything works fine except, I can not get conky to draw without a shadow in either Fluxbox or LXDE. I've tried every setting I can think of. The one that does work is if I set conky's type to Desktop but whenever I click on the desktop it disappears.

Any thoughts on this? thanks ahead of time.

---

### Post by spupy on 2012-07-10
> **loukingjr said:**
> I'm not sure if anyone can help with this or not. I installed Fluxbox in my Lubuntu 12.04 install. Since the shadows in xcompmgr broke I installed Compton. Everything works fine except, I can not get conky to draw without a shadow in either Fluxbox or LXDE. I've tried every setting I can think of. The one that does work is if I set conky's type to Desktop but whenever I click on the desktop it disappears.

Any thoughts on this? thanks ahead of time.

I use some old conky config of mine from ages ago. It draws conky without shadow in Fluxbox + Compton right now.

Here is the relevant part from the start of the conky config:

```
#!/usr/bin/conky -c
own_window true
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,sticky,skip_taskbar,skip_pager,below

use_xft yes
# Xft font when Xft is enabled
xftfont DejaVu Sans Mono:pixelsize=11
double_buffer yes
update_interval 3
draw_shades yes
draw_borders no
minimum_size 10 0
pad_percents 3
short_units yes
```


I also have this in my ".fluxbox/apps" file:
```

[app] (name=Conky) (class=Conky)
  [Layer]	{10}
[end]

```

---

### Post by loukingjr on 2012-07-10
> **spupy said:**
> I use some old conky config of mine from ages ago. It draws conky without shadow in Fluxbox + Compton right now.

Here is the relevant part from the start of the conky config:

```
#!/usr/bin/conky -c

[app] (name=Conky) (class=Conky)
  [Layer]    {10}
[end]

```

hmmm, well as I mentioned when I have conky set as "desktop" it goes invisible. perhaps the last bit of code is what I was missing. 

I still have to figure out how to fix LXDE

thanks for the info :)

---

