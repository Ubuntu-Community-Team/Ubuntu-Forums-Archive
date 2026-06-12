---
title: "Ubuntu 11.10 - Remove the login screen dot grid"
date: 2011-10-24
forum: General Help
---

### Post by xioSlayer on 2011-10-24
There is a grid of dots on the login screen in Oneiric Ocelot.

**How do you remove them?  **

I read through another topic about it but it quickly digressed into a discussion about the whether the dots were a good design decision...

Yes, the dots do look good on the default login screen, but when you change the login screen to a picture of your own it will rarely have that desired affect.




Also, as a secondary (less important) question about 11.10, I installed compiz and tried to enable the rotating cube display.  It bugged my unity desktop and I needed to reinstall it to fix.  I then saw a blog post about how this was known to happen.   If that is the case, then how does one customize 11.10 to add some cool effects?  Is the new gnome 3.2 the only option?

---

### Post by xyzzyman on 2011-10-24
The dots are hard coded in source code, so you need to track down that line of code, remove and recompile.

---

### Post by dcstar on 2011-10-25
Try:

[http://blog.sudobits.com/2011/10/06/how-to-change-login-screen-in-ubuntu-11-10/](http://blog.sudobits.com/2011/10/06/how-to-change-login-screen-in-ubuntu-11-10/)

---

### Post by jespdj on 2011-11-27
> **xyzzyman said:**
> The dots are hard coded in source code, so you need to track down that line of code, remove and recompile.
Really?

One of the features that is being advertised about LightDM (the program that manages the login screen in Ubuntu 11.10) is that it is "fully themeable"; see for example the [Launchpad page for LightDM](https://launchpad.net/lightdm) and [this article](http://www.geek.com/articles/chips/ubuntu-adopts-lightdm-login-screens-to-get-more-exciting-20110512/) saying that login screens are going to be "more exciting" in Ubuntu 11.10.

In reality there is no documentation to be found anywhere on how you could theme the login page...

---

### Post by xyzzyman on 2011-11-27
Well someone already recompiled minus the dots:

[https://launchpad.net/~scott.severance/+archive/lightdm](https://launchpad.net/~scott.severance/+archive/lightdm)

---

