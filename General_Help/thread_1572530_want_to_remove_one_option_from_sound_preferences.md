---
title: "want to remove one option from sound preferences"
date: 2010-09-11
forum: General Help
---

### Post by shantiq on 2010-09-11
[CENTER][IMG]http://img683.imageshack.us/img683/3972/23991089.png[/IMG]
[/CENTER]

i want to remove the Lapsda plugin option from my sound preferences 

how does one do that?

---

### Post by pbrane on 2010-09-11
How did this plugin get installed? There are several possible ways. Did you install **swh-plugins** from the repos? Or did you install the Pulse Audio Equalizer script from this thread:
[http://ubuntuforums.org/showpost.php?p=8210866&postcount=1]("http://ubuntuforums.org/showpost.php?p=8210866&postcount=1") ?

However it was installed you should be able to uninstall it. I'm not sure if you can simply remove it as an option. But you certainly don't have to select that option.

---

### Post by shantiq on 2010-09-11
ok pbrane thanx for reply


i installed pulseaudio-equalizer [this way]("http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/")


and have now removed the lot




so i removed  swh-plugins and when reloading sound had TOTALLY disappeared   no sound preferences left  so i had to put it back in   (are you sure the Lapsda option in sound preferences is from swh-plugins?)

underneath i show terminal reading in red might be areas of concern  maybe as regards the presence of  Lapsda plugin option in my sound preferences ??


```
shantiq@shantiq-desktop:~$ sudo apt-get remove swh-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
 [COLOR="Red"]** paprefs pavucontrol libsox-fmt-base sox pulseaudio-module-zeroconf libsox-fmt-alsa paman libsox1b pavumeter**[/COLOR]
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  swh-plugins
0 upgraded, 0 newly installed, 1 to remove and 142 not upgraded.
After this operation, 2,023kB disk space will be freed.
Do you want to continue [Y/n]?
```


so a bit confused now

---

### Post by shantiq on 2010-09-11
another way mayhaps     anyone knows which one should i remove?



[IMG]http://img651.imageshack.us/img651/7202/screenshotgcw.png[/IMG]



[IMG]http://img697.imageshack.us/img697/9775/screenshot1yuj.png[/IMG]

---

### Post by pbrane on 2010-09-11
How you installed pulseaudio equalizer is different than the way I installed it. I used the link I provided in my earlier post. It did not work for me very well so I removed it. I remember not having any sound atfer I removed it either. Even after purging it left behind some config stuff. But now that it has a PPA you should just be able to 
```

sudo apt-get --purge remove pulseaudio-equalizer

```
The install method I used created/modified a pulseaudio config file and I had to do something to correct that. Sorry I'm not much help here. I can't remember what I had to do to fix it. But after removing/editing that configure file sound worked again. I'll see if I can find the info on removing the equalizer and post back.

Also your sound preferences are in the **paprefs** package that was removed. You should be able to install it again. You can also install the **pavucontrol** package.

---

### Post by shantiq on 2010-09-11
thanx man for help


purge makes no difference the funking thing is still there
:KS:KS:KS


using pavucontrol yields this

[CENTER][IMG]http://img697.imageshack.us/img697/3649/46093002.png[/IMG][/CENTER]

i guess a diffrent way to ask the question would be how to remove a  virtual output device

---

### Post by pbrane on 2010-09-11
This is a suggested way to restore pulseaudio after removing pulseaudio-equalizer.
```

$ rm ~/.pulse -r; pulseaudio -k

```
found at
[http://ubuntuforums.org/showthread.php?t=1308838&page=26]("http://ubuntuforums.org/showthread.php?t=1308838&page=26")
in post #257.

I believe that is what I did.

---

### Post by shantiq on 2010-09-11
ok i reloaded one more time AND IT had gone do not know why but hey cool


possibly what happened is that it hung in the system after it was removed and then finally left

---

