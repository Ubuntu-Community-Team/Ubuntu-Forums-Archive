---
title: "Ubuntu doesnt load/install ?"
date: 2011-01-26
forum: General Help
---

### Post by Shwaga on 2011-01-26
Alright so I installed ubuntu 10.4 via usb onto my Acer Aspire M1640. It was running perfectly, I had my drivers installed everything was just perfect.

So I went to go download and install Java so I could play java based games, right before the installation of Java completed the whole computer just froze. Couldnt move my mouse couldnt do anything.

Keep in mind this isnt all on the first boot on ubuntu either, i had shut it down/restarted it several times because of installing drivers and such.

Anyways, so I had to shutdown the computer via holding the power button down which I am sure is not healthy for the computer at all. I went to start it up again and it just would not boot, it would either just sit there with "_" flashing in the top left of the screen, no keyboard lights on nor mouse. Or it would just keep restarting itself over and over flashing itself to the Acer screen where you press DEL to enter setup and F12 for boot menu.

So I went into Bios by pressing DEL and pressed F8 to set everything at failsafe defaults, then went into intergrated perph and disabled 1394 and audio. (I had to do this before to get ubuntu to install) saved adn exited and tried booting with these, now it just gives me this error when I try and boot..


[ 12.805282] init[1]: segfault at 1 ip es09165ff sp bfa00370 error 6 in libn:50.1.0.0[110000+12000]


So wtf? Whats going on here? What do I do?

---

### Post by Shwaga on 2011-01-26
Someone please help?

---

### Post by sikander3786 on 2011-01-26
Welcome to the forums :-)

Press and hold down Shift key from Bios screen until you see the Grub menu. Choose the second option there named Recovery and then choose failsafe graphics or safe graphics or something like this. Does it boot successfully this time?

If not, reboot and again choose recovery mode and then drop to root shell prompt. Now try these commands.

```
dhclient eth0
```

Where eth0 is your network interface.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

If there are any errors, please post them. If no errors and still your issue doesn't get sorted out, once again boot the recovery mode and from shell, post the output of these commands.

```
cat /etc/X11/xorg.conf
```

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

---

### Post by davidmohammed on 2011-01-26
this [guy has blogged]("http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/") about installing 10.04 on your model - hope it helps.

---

