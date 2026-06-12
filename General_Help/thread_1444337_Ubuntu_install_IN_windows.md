---
title: "Ubuntu install IN windows"
date: 2010-04-01
forum: General Help
---

### Post by hexn3t on 2010-04-01
Hey everyone, I recently installed ubuntu inside of windows (using the wubi.exe), and wanted to know if it is the same performance of a normal installation.

 I couldn't install it normally, some kind of cant find linux error, so I want to know if it is the same.

---

### Post by hexn3t on 2010-04-01
No one knows?

---

### Post by Nisal on 2010-04-01
what the error can u post a screen shot ?

---

### Post by mcduck on 2010-04-01
It's *almost* the same.

Even when installed with Wubi, you are never running both operating systems at the same time, Ubuntu runs on it's own just as if it was installed separately.But since Ubuntu's filesystem is actually located in a file inside a Windows file system, you'll get a small overhead from Linux having to operate every disk read/write through two filesystems instead of just one.

..and of course being located inside a Windows file system, Wubi install depends on having that file system around so in case Winbows breaks you might not be able to boot into Ubuntu any more, so you loose the benefit of having two completely separate operating systems around and being able to boot to other one if one breaks.

(The Wubi install will also be harder to fix using a live-CD, and you will probably have troubles accessing Ubuntu's files if your Windows or Ubuntu install breaks)

There are also some minor issues and bugs with Wubi installs, but they seem to be related to specific setups and situations so you probably don't need to worry about them.

What comes to the problem when installing Ubuntu in the normal way, it's hard to say anything without knowing the exact error you got. But just as a general rule, make sure the disk image you downloaded is correct (using Bittorrent downloads is a good idea, since torrent protocol will automatically check the files for you). There are plenty of tools for checking MD5 sums and you'll find the correct MD5 sum for the disk image in Ubuntu's download page. Then use some high-quality disk you know to work fine on your CD reader, and burn the disk at low speed (4x max). Finally the Ubuntu installer has built-in tool for checking the CD for defects.. :)

---

### Post by hexn3t on 2010-04-01
thanks for the help, you answered it spot on :)

I've decided I want to go ahead and try a full installation given that information using a guide | [http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html) |

---

### Post by new_tolinux on 2010-04-01
You better stick to Wubi.
Read/Write is faster from Wubi.

---

### Post by mocoloco on 2010-04-01
Read/write is NOT faster from Wubi, quite the opposite.

---

### Post by koolblue3 on 2010-04-01
Hi,

Wubi has about the same read/write speed of a normal install, but there are a couple of things to keep in mind. Here is a quote from Wubi's FAQ > 
             **Any gotcha?**

              Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.
         
                                 

---

