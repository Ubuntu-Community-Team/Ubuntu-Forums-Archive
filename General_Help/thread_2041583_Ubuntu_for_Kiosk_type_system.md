---
title: "Ubuntu for Kiosk type system"
date: 2012-08-12
forum: General Help
---

### Post by Jonny87 on 2012-08-12
I thinking about setting up a kiosk type computer for a cafe. Heres what I want to do but I need some sugestions how to set it up.

I want to use the guest account, have it to log in (this part I can do) and connect to a wireless network with out revealing or the user being possible to see the security details of the network (i.e. Password).

I want them to have acess to a variety of apps such as multiple web browsers (so they can use there browser of choice exclding IE). but limited so that they can't gain access to administrative rights or change the system in anyway. Which I'm sure is the case with the guest account, but is there any other tweaks that can be made to further secure it.

Either remove the ability to restart the comp from both the logged in session and the login screen, or stop them accessing the recovery options on startup with root access.

---

### Post by lykwydchykyn on 2012-08-12
This is an article I wrote a while back, it (and the comments following) may have some helpful points for you:

[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)

---

### Post by bodhi.zazen on 2012-08-12
> **Jonny87 said:**
> I thinking about setting up a kiosk type computer for a cafe. Heres what I want to do but I need some sugestions how to set it up.

I want to use the guest account, have it to log in (this part I can do) and connect to a wireless network with out revealing or the user being possible to see the security details of the network (i.e. Password).

I want them to have acess to a variety of apps such as multiple web browsers (so they can use there browser of choice exclding IE). but limited so that they can't gain access to administrative rights or change the system in anyway. Which I'm sure is the case with the guest account, but is there any other tweaks that can be made to further secure it.

Either remove the ability to restart the comp from both the logged in session and the login screen, or stop them accessing the recovery options on startup with root access.

I would use a kiosk specific distro, why re-create the wheel ?

[http://webconverger.com/](http://webconverger.com/)

Fedora also does a kiosk spin where the guest account is confined by selinux, very secure.

[http://spins.fedoraproject.org/kiosk/#home](http://spins.fedoraproject.org/kiosk/#home)

I am not sure if it is maintained, you could ask on #fedora

---

### Post by Jonny87 on 2012-08-13
Thanks bodhi.zazen, I have seen wbconverge but it is only a web browser. will look into the fedora one though thanks.

---

### Post by Jonny87 on 2012-08-18
Ok so I'm still looking over ideas and so far the pre built systems dont do what I want, I want them to have more the a web browser. I want them to have almost a full Ubuntu. I've got some ideas on how i'm going to do it. there's still a cupple of things I need to know that I'm having trouble finding out.

firstly is there a way to edit the Unity Applications Menu to remove certain apps on a per user bases so that the user can't access them?

secondly I want run a script when the user, say "guest", logs in, but it needs to run with the sudo/root privileges of the admin, but have no possible way that the gust see or access it.

---

### Post by lykwydchykyn on 2012-08-18
> **Jonny87 said:**
> 
firstly is there a way to edit the Unity Applications Menu to remove certain apps on a per user bases so that the user can't access them?

I can't say authoritatively, but I really doubt Unity has the features to make this happen.  It's a relatively young project, and AFAIK there is no kiosk-mode for it right now.

You could try to hack it by making the unity config file (whatever the file is) read-only, but that could cause it to crash.

> 
secondly I want run a script when the user, say "guest", logs in, but it needs to run with the sudo/root privileges of the admin, but have no possible way that the gust see or access it.

You can configure sudo to allow a user to run only specific executables as root with no password prompt.  This is how you'd ideally go about doing it.  You'd want to assign this privilege to the Guest group, since guest users are auto-generated and unique.

The line to add to sudoers looks something like this:
```

%Guest  All = (All) NOPASSWD: /path/to/my/script

```

Then put your script somewhere like /opt or /usr/local, make it owned by root, with permissions 700.

---

### Post by unevenflow on 2012-08-18
Hey, perhaps a combination of 
LTSP 
[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)
[https://help.ubuntu.com/community/UbuntuLTSP/](https://help.ubuntu.com/community/UbuntuLTSP/)
and GOFRIS 
[http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html](http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html)
[http://xubuntugeek.blogspot.gr/2012/07/how-to-deep-freeze-xubuntu-with-ofris.html](http://xubuntugeek.blogspot.gr/2012/07/how-to-deep-freeze-xubuntu-with-ofris.html)
is what you need

---

### Post by Jonny87 on 2012-08-18
> **lykwydchykyn said:**
> I can't say authoritatively, but I really doubt Unity has the features to make this happen.  It's a relatively young project, and AFAIK there is no kiosk-mode for it right now.

You could try to hack it by making the unity config file (whatever the file is) read-only, but that could cause it to crash.



You can configure sudo to allow a user to run only specific executables as root with no password prompt.  This is how you'd ideally go about doing it.  You'd want to assign this privilege to the Guest group, since guest users are auto-generated and unique.

The line to add to sudoers looks something like this:
```

%Guest  All = (All) NOPASSWD: /path/to/my/script

```Then put your script somewhere like /opt or /usr/local, make it owned by root, with permissions 700.

Thanks, I'll look into your idea for the scripts.

---

### Post by Jonny87 on 2012-08-18
> **unevenflow said:**
> Hey, perhaps a combination of 
LTSP 
[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)
[https://help.ubuntu.com/community/UbuntuLTSP/](https://help.ubuntu.com/community/UbuntuLTSP/)
and GOFRIS 
[http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html](http://www.upubuntu.com/2011/07/install-gofris-on-ubuntu-1104-to.html)
[http://xubuntugeek.blogspot.gr/2012/07/how-to-deep-freeze-xubuntu-with-ofris.html](http://xubuntugeek.blogspot.gr/2012/07/how-to-deep-freeze-xubuntu-with-ofris.html)
is what you need

Yea I have come across the LTPS as well as GOFRIS, I'm not sure that I don't really have the hardware to set up server to point a thinclient to. One of the reasons I want to use linux is the fact that it's low cost. I need a low cost solution in the mean time to get things going, the down the track if I have the money, i can look at the idea of server and stuff.

---

### Post by lykwydchykyn on 2012-08-18
XFCE has a pretty robust kiosk framework, at least I've heard so.  I haven't messed with it myself.

KDE also has a kiosk framework, and you could probably emulate some of the layout of Unity (or whatever layout you want) using different plasmoids.  The downside is that it involves a lot of config-file hacking.  More info here: [http://techbase.kde.org/KDE_System_Administration/Kiosk/Introduction](http://techbase.kde.org/KDE_System_Administration/Kiosk/Introduction)

If you go to the link I first gave you, there's a link at the bottom to a full-screen tabbed menu that I've been developing for application-based kiosks.

Don't know if any of that helps, but it gives you some options.  Being able to lock down a desktop is something that requires pervasive support built into the DE, and Unity just doesn't have it yet.

---

