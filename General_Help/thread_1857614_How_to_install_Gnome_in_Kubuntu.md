---
title: "How to install Gnome in Kubuntu"
date: 2011-10-10
forum: General Help
---

### Post by Simeo on 2011-10-10
On this Ubuntu install I thought I'd try the KDE flavor of Ubuntu out. I like KDE, but I'm intensely annoyed on a regular basis with figuring out how to do what should be simple things. Not only that, it's much easier to find Gnome style tutorials to do things than KDE style tutorials.

I just want my old Ubuntu back... but I spent a long time installing all the software I needed again (Gimp, Virtualbox, Chromium, Firefox, etc etc etc) and I don't want to lose all my programs or settings again and spend another 4 days reconfiguring. 

Is there any way I could dump KDE and go back to Gnome or conveniently push KDE under the rug and in the user login choose the Gnome style? I'm not too concerned with HD space (I have 500GB).

---

### Post by snowpine on 2011-10-10
You might find this tutorial helpful:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Good luck! :)

---

### Post by Simeo on 2011-10-10
> **snowpine said:**
> You might find this tutorial helpful:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Good luck! :)

The output:

```
[sudo] password for: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ktimetracker is not installed, so not removed
Package libvncserver0 is not installed, so not removed
Package nepomukcontroller is not installed, so not removed
Package pinentry-gtk2 is not installed, so not removed
Package kdebase-data is not installed, so not removed
Package kdebase-runtime-data is not installed, so not removed
Package kdebase-workspace-bin is not installed, so not removed
Package kdebase-workspace-data is not installed, so not removed
Package kdebase-workspace-kgreet-plugins is not installed, so not removed
Package libkdegames5 is not installed, so not removed
Package libkonq5a is not installed, so not removed
Package libpowerdevilcore0 is not installed, so not removed
Package libtaskmanager4b is not installed, so not removed
Package plasma-scriptengine-declarative is not installed, so not removed
Package krfb is not installed, so not removed
Package krdc is not installed, so not removed
Package oxygen-icon-theme-complete is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages

```

So.... this didn't work?

---

### Post by snowpine on 2011-10-10
Are you following the correct instructions for your release (11.04, 10.10, etc)?

---

### Post by Simeo on 2011-10-10
> **snowpine said:**
> Are you following the correct instructions for your release (11.04, 10.10, etc)?

Yep. I have Kubuntu 11.04

---

### Post by ajgreeny on 2011-10-10
What version of ubuntu was it originally?  Did you choose the correct command from that psychocats site for your version?

---

### Post by Simeo on 2011-10-10
> **ajgreeny said:**
> What version of ubuntu was it originally?  Did you choose the correct command from that psychocats site for your version?

Yep. I have Kubuntu 11.04

---

### Post by snowpine on 2011-10-10
Look at this part:

```

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages

```

That part caught my eye, so I did a forum Search:

[http://ubuntuforums.org/showthread.php?t=1733366](http://ubuntuforums.org/showthread.php?t=1733366)
[http://ubuntuforums.org/showthread.php?t=1579169&page=2](http://ubuntuforums.org/showthread.php?t=1579169&page=2)

I hope that helps you, I don't have a Kubuntu system myself to test it for you. ;)

---

### Post by Simeo on 2011-10-10
> **snowpine said:**
> Look at this part:

```

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not installable
E: Broken packages

```

That part caught my eye, so I did a forum Search:

[http://ubuntuforums.org/showthread.php?t=1733366](http://ubuntuforums.org/showthread.php?t=1733366)
[http://ubuntuforums.org/showthread.php?t=1579169&page=2](http://ubuntuforums.org/showthread.php?t=1579169&page=2)

I hope that helps you, I don't have a Kubuntu system myself to test it for you. ;)

Awesome. Finally got everything to work with the second link. Thanks guys for the help. I'm now back to Gnome/Unity

---

### Post by Haneef Mubarak on 2011-10-10
Just do this:

```

sudo apt-get --purge remove ubuntu-desktop; sudo apt-get install ubuntu desktop

```

Hope that helps! :popcorn:

---

