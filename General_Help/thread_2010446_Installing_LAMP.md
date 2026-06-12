---
title: "Installing LAMP"
date: 2012-06-25
forum: General Help
---

### Post by dauber on 2012-06-25
So...I want to set up LAMP and use my Ubuntu box as a private web server, mainly to test PHP, MySQL, et al.

Do I need to install Ubuntu Server for that, or is just the plain ol' non-server Ubuntu 12.04 distro suitable enough?

---

### Post by bab1 on 2012-06-25
> **dauber said:**
> So...I want to set up LAMP and use my Ubuntu box as a private web server, mainly to test PHP, MySQL, et al.

Do I need to install Ubuntu Server for that, or is just the plain ol' non-server Ubuntu 12.04 distro suitable enough?

If you install Ubuntu Server be prepared to do everything from CLI.  No comfy GUI interface is installed with the Server Edition.

If you want the GUI then install the Desktop and then install LAMP.  [**_[COLOR="Blue"]Here[/COLOR]_**]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/") is a Blog post about how to do just that.

You won't suffer any performance loss using the Desktop Edition

---

### Post by holycow131415 on 2012-06-25
plan old ubuntu is fine. id use xubuntu or lubuntu so that unity doesnt use more resources. i would use xampp to install your webserver into /opt. its nice and easy.

---

### Post by sandyd on 2012-06-25
> **dauber said:**
> So...I want to set up LAMP and use my Ubuntu box as a private web server, mainly to test PHP, MySQL, et al.

Do I need to install Ubuntu Server for that, or is just the plain ol' non-server Ubuntu 12.04 distro suitable enough?
There is actually no difference between Ubuntu Server, and Ubuntu, other than the fact that Ubuntu Server has no gui. You can run Apache on Ubuntu just as well as you can run it on Ubuntu Server.

I would not do that for production purposes however.

---

### Post by Cheesemill on 2012-06-25
> **holycow131415 said:**
> i would use xampp to install your webserver into /opt. its nice and easy.

I would recommend against this, you're much better off installing Apache, MySQL and PHP from the Ubuntu repositories instead by just doing:
```
sudo apt-get install lamp-server^
```(The caret isn't a typo).

This method ensures that they stay up to date with the rest of your system as well as all the configuration files being in the correctly documented locations.

---

### Post by sandyd on 2012-06-25
> **Cheesemill said:**
> I would recommend against this, you're much better off installing Apache, MySQL and PHP from the Ubuntu repositories instead by just doing:
```
sudo apt-get install lamp-server^
```(The caret isn't a typo).

This method ensures that they stay up to date with the rest of your system as well as all the configuration files being in the correctly documented locations.
You can select this in
```

sudo tasksel
```
as well.

---

### Post by nipunshakya on 2012-06-25
@op: please refer to the link below... this will help you out..
[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

Goodluck

---

### Post by bab1 on 2012-06-25
> **WinuxUser said:**
> @op: please refer to the link below... this will help you out..
[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

Goodluck

As I linked to in post #2.  :-)

---

### Post by nipunshakya on 2012-06-25
ohh... sorry for the duplicate link bab1... didnt notice it seriously... very sorry

---

### Post by Damascushead on 2012-06-25
Don't worry too much about resource use from LAMP. I am running a small lamp server for the exact purposes you describe...learning php and sql and I am running it on 2GB ram, dual core and it runs just fine (running 12.04). 

Go for It!

---

### Post by dauber on 2012-08-06
Hey, everyone...sorry for the late reply, but thanks for your input! Got LAMP going on my Linux box...that eventually had a "thermal event" ...arrghh! So I put Ubuntu on another PC and got LAMP going there instead. :)

---

