---
title: "ypops or fetchyahoo help?"
date: 2006-02-23
forum: General Help
---

### Post by fireburns on 2006-02-23
Hello all,

I've been experimenting with several new distros over the last couple of weeks, and I think I'm settling in on Kubuntu.

In the past, I used Fedora Core 3, but so far I seem to like Debian based distro's better.

However, I would like to check both my ISP mail and my yahoo e-mail via and e-mail application such as Thunderbird.  Under FC3 I was able to install via RPM a utility called ypops.  I tried installing the rpm via alien and dpkg, but that doesn't seem to have worked.  I don't have the skills to manually compile the source, so I'm stuck.  In reading through the install instructions, I know I need to a) edit the Makefile to reflect the correct paths.  Unfortunately, I do not know the correct paths or how to determine them.  and b) download and install mime

I also know that fetchyahoo is another option, but while I have installed it via adept, I have no idea what to do from here.  I found this thread:

[http://www.ubuntuforums.org/showthread.php?t=38757&highlight=ypops](http://www.ubuntuforums.org/showthread.php?t=38757&highlight=ypops)

but it refernces a spool which I do not have...my /var/spool directory is emply.  Additionally, what e-mail client should I be using with fetchyahoo?  Evolution is what's referenced, but wouldn't I end up installing Gnome to install evolution?

Thanks for giving some help to a newb....

---

### Post by fireburns on 2006-02-25
For those curious, I found an app called "freepops" ([http://www.freepops.org/en/](http://www.freepops.org/en/)) that did the trick.

---

### Post by msak007 on 2006-02-26
[This]("http://webmail.mozdev.org/") might help you. I'm using the WebMail extension, in conjunction with the Hotmail and Yahoo extensions, to check email using Thunderbird. Not only that, but you can send email using Thunderbird as well using that email address. It's worked great so far.

---

### Post by AmandaKerik on 2007-02-01
I used to use ypops, and I find the webmail add-on much easier to set up, etc. :KS

When they say set a port over 1024, they mean it - I used 1111 and 1112. Works like a charm!

---

### Post by tskariah on 2007-05-15
I have built a package for Ubuntu (and other Debian based OS) for easy installation without having to compile from the source.

You could access it from here: [ypops_0.8.8.-1_i386.deb]("http://www.geocities.com/t_skariah/ypops/")

---

### Post by manno on 2007-06-28
> **tskariah said:**
> I have built a package for Ubuntu (and other Debian based OS) for easy installation without having to compile from the source.

You could access it from here: [ypops_0.8.8.-1_i386.deb]("http://www.geocities.com/t_skariah/ypops/")

That install package works great! Thanks for posting it here on the forums!

---

