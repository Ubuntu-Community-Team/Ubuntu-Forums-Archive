---
title: "Cannot install Sun java 6 package from u9.10 s/w center"
date: 2009-10-30
forum: General Help
---

### Post by FrostCake on 2009-10-30
Could not install sun java 6 brower plugin from ubuntu s/w center.

Tried the terminal 

sudo apt-get install sun-java6-plugin

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

```

---

### Post by dj-toonz on 2009-10-30
Do you have all the updates enabled & the karmic partner enabled in software sources? 

Here's the command I used to install sun Java

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

worked for me :popcorn:

---

### Post by FrostCake on 2009-10-30
Wow that was speedy. Thanks dj.

Unfortunately it did not work for me :(. 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but 6-16-0ubuntu1.9.04 is to be installed
E: Broken packages

```

I don't really know what unmet dependencies in the last 5 lines meant.

---

### Post by dj-toonz on 2009-10-30
I haven't a clue as to what's up as I installed it on a fresh Install with nothing else on the system & it installed no problems, sorry I couldn't help :( somebody else might be able help you better then I can (just thought of something, have you tried sudo apt-get -f install) or going into synapic Package Manager & clicking on custom Filters, Broken & posting what Packages it shows up, then I might be able to sort this out

---

### Post by FrostCake on 2009-10-30
I'm not too sure myself haha :D Still looking around for the solution. 

Thanks again.

---

### Post by mhh91 on 2009-10-30
Is that a fresh install or an upgrade ?


the plugin installed properly on my virtualbox installation of 9.10 using s/w center

---

### Post by FrostCake on 2009-10-30
Ok fixed. Was an upgrade fr. u/unb 9.04. Happened to both my desktop and netbook, so its probably some systemic bug.

I uninstalled with:
sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts
sudo apt-get autoremove

Cleared the installed (residuals) in synaptic manager.
Rebooted.

Installed sun-java6-plugin from the Ubuntu S/w Center.

Thanks guys :)

---

### Post by viktormas on 2009-11-04
> **FrostCake said:**
> Ok fixed. Was an upgrade fr. u/unb 9.04. Happened to both my desktop and netbook, so its probably some systemic bug.

I uninstalled with:
sudo apt-get remove sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts
sudo apt-get autoremove

Cleared the installed (residuals) in synaptic manager.
Rebooted.

Installed sun-java6-plugin from the Ubuntu S/w Center.

Thanks guys :)

This solution worked for me either, was 9.04 previously. Thanks

---

### Post by ewoutterhaar on 2009-11-07
Same here: 9.10, upgraded from 9.04, gave a broken package warning. After removing and re-installing all sun-java packages, everything is ok.

---

### Post by rhythman on 2010-01-16
> **ewoutterhaar said:**
> Same here: 9.10, upgraded from 9.04, gave a broken package warning. After removing and re-installing all sun-java packages, everything is ok.
Ditto for me.

---

### Post by Murdock304 on 2010-03-13
Same here

---

### Post by scouser73 on 2010-03-13
For installing the latest 32 & 64 bit version of Java please follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by YeeP on 2010-06-02
Worked for me too. Thanks! :guitar:

---

