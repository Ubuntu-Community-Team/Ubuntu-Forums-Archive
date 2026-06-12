---
title: "Kiosk changes"
date: 2012-09-17
forum: General Help
---

### Post by divisionmd on 2012-09-17
Hello,

Installed Ubuntu 12.04 - and happy with everything on how it works!

Going to have this machine running a webpage in a recption.

And want to remove all buttons/dialogs (notice of new updates) and more.

So the computer is as clean as possible - and only shows a webpage.

Can someone give me ideas / on what services to remove? will run the computer like "kiosk" installation.

For example removing cupsd... 

Thanks for help,

Best regards,
Johan

---

### Post by Lars Noodén on 2012-09-17
Here's a very good description of setting up a Linux kiosk:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

---

### Post by Merrattic on 2012-09-17
If you are planning on display only (no interaction) and the webpage is static in content, consider using feh to run the image to fullscreen. You can also do a similar thing without running X at all, but using the framebuffer to display an image/slideshow

---

### Post by divisionmd on 2012-11-13
Thanks everyone,

- Will read through that link posted.

Best regards,

Johan

---

### Post by oldfred on 2012-11-13
Several links from my files. Including the one by Lars.

Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)
[http://spins.fedoraproject.org/kiosk/#home](http://spins.fedoraproject.org/kiosk/#home)
Older
[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm)
[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition](http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition)

---

