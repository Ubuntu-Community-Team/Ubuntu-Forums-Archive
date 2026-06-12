---
title: "Splash screen in ubuntu 9.10"
date: 2010-02-10
forum: General Help
---

### Post by jordan86 on 2010-02-10
The screen that with the background pic at below is it call splash screen?
[img]http://news.softpedia.com/images/extra/LINUX/small/ubuntu910alpha6-small_000.png[/img]

How to change the screen at above to text based that shows what services have been started, and if the service has been started, it will show ok at the right side. How to do that? Thanks.

---

### Post by byStanderone on 2010-02-10
...give this a try:

Follow the steps below to disable the splash screen.
1. Edit grub.

 $ sudo gedit /etc/default/grub

Locate the following line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Remove quiet and splash
Now the line should look like this

GRUB_CMDLINE_LINUX_DEFAULT=""

Now save and exit.

2. Now update the grub.

$ sudo update-grub

---

### Post by jordan86 on 2010-02-10
> **byStanderone said:**
> ...give this a try:

Follow the steps below to disable the splash screen.
1. Edit grub.

 $ sudo gedit /etc/default/grub

Locate the following line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

Remove quiet and splash
Now the line should look like this

GRUB_CMDLINE_LINUX_DEFAULT=""

Now save and exit.

2. Now update the grub.

$ sudo update-grub


Yup, I did that before.
It only changed everything to text based BEFORE the image above. It does not show what services have been started.

---

