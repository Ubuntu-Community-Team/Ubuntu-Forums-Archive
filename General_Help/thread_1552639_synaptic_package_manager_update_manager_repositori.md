---
title: "synaptic package manager/ update manager repositories oddness 10.04 lucid 64bit"
date: 2010-08-13
forum: General Help
---

### Post by samcoinc on 2010-08-13
I am having an odd issue.. when I go into the synaptic package manager and go setting -> repositories - nothing happens. No popup opens allowing me to change or add repositories.  it just goes back to the synaptic package manager.  Initially it said - repositorys have changed reload - but I checked the 'don't show again' box.  now it just doesn't do anything.

also - in the update manager - if I click on 'settings' in the lower left also nothing happens.  a popup comes up saying  'reading package information' and under that says 'building data structures' but then goes right back to the update manager.  Odd huh?

thanks
sam

---

### Post by wojox on 2010-08-13
#1 What happens if you open System > Admin > Software Sources. You can also add ppa from the command line.

> but I checked the 'don't show again' box.

Never seen that before.

#2 Open your terminal and run:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by samcoinc on 2010-08-13
When I click on the software sources - I get the same thing - nothing :) odd.


> **wojox said:**
> #1 What happens if you open System > Admin > Software Sources. You can also add ppa from the command line.



Never seen that before.

#2 Open your terminal and run:

```
sudo apt-get update; sudo apt-get upgrade
```

this is what I get when I do that - looks right...

```
samco@samco-laptop:~$ sudo apt-get update; sudo apt-get upgrade
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
samco@samco-laptop:~$
```

---

### Post by wojox on 2010-08-13
Well it appears there are no updates for you.

As far as Software Sources how about going through Update Manager > Settings ? Does that bring it up?

---

### Post by samcoinc on 2010-08-13
nope - same thing.  Maybe wait for the next batches of updates and see if it is fixed? 

thanks
sam

> **wojox said:**
> Well it appears there are no updates for you.

As far as Software Sources how about going through Update Manager > Settings ? Does that bring it up?

---

### Post by mc4man on 2010-08-13
You could try from the terminal and see if it works or you get any error message 
```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
```

---

### Post by samcoinc on 2010-08-13
Heh! 

samco@samco-laptop:~$ gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
samco@samco-laptop:~$ 

nothing opens - no errors.  Top that! ;)

thanks
sam


> **mc4man said:**
> You could try from the terminal and see if it works or you get any error message 
```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
```

---

### Post by wojox on 2010-08-13
> **mc4man said:**
> You could try from the terminal and see if it works or you get any error message 
```
gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
```

That's the command I was looking for to open it from the terminal?  :)

---

### Post by samcoinc on 2010-08-16
So - I did an sudo apt-get update; sudo apt-get upgrade and that seems to work normally.  But I still cannot get into any of the repository gui (through update manager, synaptic, or software sources.)

Could there be something wrong with my repository file or something?

thanks
sam

---

### Post by samcoinc on 2010-08-16
mc4man: 

I did find out that if I run your command twice - the first time it asks for the sudo password then nothing - the second time I do get an error.

samco@samco-laptop:~$ gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
samco@samco-laptop:~$ gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named softwareproperties.gtk.SoftwarePropertiesGtk
samco@samco-laptop:~$

---

### Post by samcoinc on 2010-08-16
I had found this 

[http://ubuntuforums.org/showthread.php?t=1425243&highlight=softwareproperties](http://ubuntuforums.org/showthread.php?t=1425243&highlight=softwareproperties)

but it doesn't seem to apply 

sam

---

### Post by samcoinc on 2010-08-18
wow - I was talking to a friend on irc and we tried a few things - the thing that fixed it was 

sudo aptitude reinstall python-xkit python-software-properties

Now all the gui repository managers work (synaptic, software sources, update manager.)

thanks guys.

---

### Post by Jetro on 2010-10-20
I am having the exact same problem as you, and nothing seems to be working for me, not even the suggestion in your last post. :/

---

### Post by Jetro on 2010-10-22
And now Ubuntu Software Center won't open... what is happening?

---

