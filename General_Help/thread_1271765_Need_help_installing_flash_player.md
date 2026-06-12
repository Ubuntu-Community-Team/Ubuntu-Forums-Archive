---
title: "Need help installing flash player"
date: 2009-09-21
forum: General Help
---

### Post by trailerkn on 2009-09-21
I have a problem when i try to install Adobe flash player on my ubuntu laptop.

when i open the folder i have downloaded, extracted the "libflashplater.so" to the dekstop and clicks on the only file in the folder : "libflashplayer.so" i get a error message : 

"Could not display "/home/kristoffer/.cache/.fr-zXtJJD/libflashplayer.so"
the location is not a folder"

please help!

---

### Post by beastrace91 on 2009-09-21
It always easiest to install software via apt-get when ever possible. Open terminal (Applications->Accessories->Terminal) and run the following command: ```
sudo apt-get install ubuntu-restricted-extras
``` It will install Adobe Flash among other useful things you might need along the way (Java ect.)

~Jeff

---

### Post by NoaHall on 2009-09-21
Follow the advice in my sig. (I think you're installing 64 bit alpha flash right?)

---

### Post by snowpine on 2009-09-21
Beastrace91 is correct. If you just want the flash plugin (and not the other restricted extras) the command is:

```
sudo apt-get install flashplugin-nonfree
```

The application repository is one of the best parts of Ubuntu; might as well use it. :)

---

### Post by jerrrys on 2009-09-21
this is what you will end up with

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by trailerkn on 2009-09-22
yeah, but everytime i try to install something with the "terminal i get this error message:

kristoffer@kristoffer-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for kristoffer: 
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
E: Klarte ikke å finne pakken flashplugin-nonfree
kristoffer@kristoffer-laptop:~$ 

translation "E: was not able to find package flashplugin-nonfree"

---

### Post by Bucky Ball on 2009-09-22
What about when you try 

```
sudo apt-get install ubuntu-restricted-extras
```... as suggested by beastrace91, which will also load it. Same problem?

---

### Post by snowpine on 2009-09-22
Try doing this first:

```
sudo apt-get update
```

---

### Post by 3rdalbum on 2009-09-22
If the OP is using 64-bit, he/she does NOT want the 32-bit plugin from the repositories.

You need to drag the "libflashplayer.so" file to either /usr/lib/mozilla/plugins or /.mozilla/plugins.

If you want to put it into /usr/lib/mozilla/plugins, then you need to open a root file browser by running "gksudo nautilus" in a terminal.

---

### Post by trailerkn on 2009-09-23
i get a error message every time i try to do what your saying with the terminal i get this: 

kristoffer@kristoffer-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for kristoffer: 
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
E: Klarte ikke å finne pakken ubuntu-restricted-extras

Translation : 

Reading packagelists....finish
Creating [FONT=Arial][COLOR=#000000]overview over (?addictedrelasionship?)
Reading [/COLOR][/FONT][FONT=Arial][COLOR=#000000]conditioninformation...finish
E:was not able to find package ubuntu-restricted-extras
[/COLOR][/FONT]

---

### Post by scouser73 on 2009-09-23
[COLOR="Red"]**Installing Flash Player via the Adobe website.**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

---

### Post by 3rdalbum on 2009-09-23
> **trailerkn said:**
> 
E:was not able to find package ubuntu-restricted-extras


You need to reload your package list then, by clicking the Reload button in Synaptic, or running the command:

```
sudo apt-get update
```

Of course this requires an internet connection.

---

### Post by trailerkn on 2009-09-24
when i try to download the drop down .deb for ubuntu 8.04+, saved it to the desktop and opened it with GDebi package installer, it comes and error when i have open the progran : Error: Dependency is not satisfiable: libnspr4-dev

---

### Post by fluffman86 on 2009-09-24
Go to System > Administration > Software Sources and put a checkmark next to the top four boxes.  When you close the Software Sources window, it will ask if you want to "Reload" and you should allow it to do so.

Then you should be able to run "sudo apt-get install ubuntu-restricted-extras"

---

### Post by Bucky Ball on 2009-09-24
You might also try:

```
sudo apt-get install libnspr4-dev
```

---

### Post by trailerkn on 2009-09-24
Thanks guys for helping me out, when i was out and comes back to my computer a screen popped up with updates, like 230 updates, fixed errors updates. from a program called : update manager.

after i did that, i can install everything without any problems

thanks mates ! :popcorn:

---

