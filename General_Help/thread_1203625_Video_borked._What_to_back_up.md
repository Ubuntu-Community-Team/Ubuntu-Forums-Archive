---
title: "Video borked. What to back up?"
date: 2009-07-03
forum: General Help
---

### Post by Nyken on 2009-07-03
Hi,

Tried to install a Diamond Fire GL3000 into a fairly new computer I found and had nothing but trouble to get it to work. Lspci found 3 chipsets in the things and everything I read to configure it manually in xorg.conf under those conditions worked. So I took it out and gave up and decided to go back to the onboard intel video. 

To the best of my knowledge, I put everything back to the way it was, but I keep getting a black screen at the login screen. Best so far I am able to get is login at the command line, by speecifiing the driver in Xorg.conf. When I first installed Ubuntu, my xorg.conf only listed identifiers in the sections with no other additions and everything worked perfectly. Example:

Section "Device"
           Identifier "Configured Video Device"
EndSection

I put Usplash back to the way it was when I began. I reran update-initramfs several times to put things back. But I still get the black screen.

So, right now I just want to know what to back up so my applications, home folder, and desktop theme can be restored to what they were after I reinstall Jaunty. I have an old backup tarball, but it's missing some things. So, I plan on using the tar -cvpfz route to back it all up to the second hard drive.

What directories should I back up to achieve this? I figure /bin and /usr have most of what I'd need. Basically, I want to be able to unpack the tarball after reinstall and get back to where I left off.

I'll try again, (yeah, I'm stupid like that) after I get a usuable backup again.

Thanks in advance! ;)

---

### Post by blueridgedog on 2009-07-03
Before you give up, you could try and reconfigure the X server.  rename your existing config file to Xorg.conf.save then try:

```
CTRL+ALT+F1 -> to get to a terminal
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

