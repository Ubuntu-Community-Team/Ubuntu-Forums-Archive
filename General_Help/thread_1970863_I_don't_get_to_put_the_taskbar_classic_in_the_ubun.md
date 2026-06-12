---
title: "I don't get to put the taskbar classic in the ubuntu 12.04 of 64 bits"
date: 2012-05-01
forum: General Help
---

### Post by TSalvio on 2012-05-01
Hello!

I just instaled the Ubuntu 12.04 but i can't get it to work with the classic taskbar of the Gnome. 

When I try, i can't edit it because I can't click with the right button of the mouse. 

What's the solution to this problem?

---

### Post by nothingspecial on 2012-05-03
prefix changed from lubuntu to ubuntu

---

### Post by cortman on 2012-05-03
> **TSalvio said:**
> Hello!

I just instaled the Ubuntu 12.04 but i can't get it to work with the classic taskbar of the Gnome. 

When I try, i can't edit it because I can't click with the right button of the mouse. 

What's the solution to this problem?

Alt + right click.

---

### Post by TSalvio on 2012-05-03
> **cortman said:**
> Alt + right click.

I could not even then did not work.

---

### Post by Cheesemill on 2012-05-03
Try SUPER+ALT+Right-Click

---

### Post by KeLa on 2012-05-03
Did you do that
```
sudo yum install gnome shell
```
and after that logoff and from login screen click icon after your username and select gnome classic
After that you have gnome and you can start modify it.

---

### Post by philinux on 2012-05-03
> **KeLa said:**
> Did you do that
```
sudo yum install gnome shell
```
and after that logoff and from login screen click icon after your username and select gnome classic
After that you have gnome and you can start modify it.

YUM is for RPM not debian based distros files. 

And it would be,for 12.04. ```
sudo apt-get install gnome-panel
```

Which by reading post one the OP must already have done.

---

### Post by KeLa on 2012-05-03
Just checked from one of my 12.04 virtual box installations and that
```
sudo apt-get install gnome-shell
```
works also...
Sorry about that yum mixup (using only rhel on work)

---

### Post by TSalvio on 2012-05-03
> **Cheesemill said:**
> Try SUPER+ALT+Right-Click

Now get! Thank you all!

---

