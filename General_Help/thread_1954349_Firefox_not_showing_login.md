---
title: "Firefox not showing login"
date: 2012-04-07
forum: General Help
---

### Post by jones27557 on 2012-04-07
I am running firefox on ubuntu 11.10 alongside Windows 7.

When I go to my webpage in Internet Explorer the page opens for the login properly.  When I go there on Firefox, it doesn't show the option to login.

I'm guessing it is something with the security settings not allowing the script to run but I cannot find any settings for it.

When I go here:  [http://jones27557.lorexddns.net](http://jones27557.lorexddns.net)   A login screen should appear where I enter my user name/password but it shows only the page header logo and a blank white screen.

Thanks!

---

### Post by lovinglinux on 2012-04-08
That's because the page you are trying to see uses ActiveX plugin. You can view that only with Internet Explorer.

[http://en.wikipedia.org/wiki/ActiveX](http://en.wikipedia.org/wiki/ActiveX)

---

### Post by jones27557 on 2012-04-20
OK.  That makes sense.  I guess I can't use my laptop with my security camera stuff.

BUT, it is possible to have a windows machine running the activeX and then somehow do a desktop sharing type thing and see whats on the windows machine screen with my ubuntu machine?  Like I could have my windows box logged into my camera stuff and showing the cameras on the windows box screen.

Or would doing that require active x to make that happen?

---

### Post by lovinglinux on 2012-04-21
> **jones27557 said:**
> OK.  That makes sense.  I guess I can't use my laptop with my security camera stuff.

BUT, it is possible to have a windows machine running the activeX and then somehow do a desktop sharing type thing and see whats on the windows machine screen with my ubuntu machine?  Like I could have my windows box logged into my camera stuff and showing the cameras on the windows box screen.

Or would doing that require active x to make that happen?

It is possible. You could also run Windows on a virtual machine with VirtualBox. It has a seamless mode, that allows you to "overlay" the guest OS applications on top of the host, so you don't feel like running a virtual machine.

---

