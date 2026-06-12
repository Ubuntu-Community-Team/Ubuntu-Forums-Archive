---
title: "Ubuntu rollback"
date: 2009-12-03
forum: General Help
---

### Post by horseradish on 2009-12-03
Is there a way to rollback ubuntu in the manner Windows does ? Either inkscape or kdenlive have altered my gstreamer and being able to rollback to how it was before would solve my problem. 

Rollback would seem more necessary for linux rather than windows.

---

### Post by jegerjensen on 2009-12-03
How did the change happen?  If you think there was a change introduced by the update-manager, you should be able to reverse it by downgrading the packages with synaptic.

What is the problem, and why do you think inkscape or kdenlive caused it?

---

### Post by horseradish on 2009-12-03
> **jegerjensen said:**
> How did the change happen?  If you think there was a change introduced by the update-manager, you should be able to reverse it by downgrading the packages with synaptic.

What is the problem, and why do you think inkscape or kdenlive caused it?

Nothing that relies on gstreamer worked after I installed both programs. I think it was kdenlive actually. I'm sure its a conflict but I don't know what.

How would I downgrade gstreamer ? It was ok in koala until I installed kdenlive

---

### Post by jegerjensen on 2009-12-03
To downgrade something you open synaptic select the package and choose Package->Force version or something similar from the menu.  (Mine is in norwegian, so I don't know the exact wording in english.)

However, since you believe that it was triggered by installation of kdenlive, and not the update to a new version, the simplest check would be to just uninstall kdenlive and see if the problem goes away.  

To remove all dependencies of kdenlive you may need to run
```
[...]$sudo apt-get autoremove
```

(I am not sure if synaptic can do that for you)

---

### Post by gadolinio on 2009-12-03
To downgrade or uninstall packages, go to system-->administration-->synaptic package manager. Search for the package you regret having installed/upgraded, right click it and choose the option you like. You might well uninstall it and then install another version, i.e. a previous one (but be sure you know what package you're selecting).

---

### Post by horseradish on 2009-12-03
> **jegerjensen said:**
> To downgrade something you open synaptic select the package and choose Package->Force version or something similar from the menu.  (Mine is in norwegian, so I don't know the exact wording in english.)

However, since you believe that it was triggered by installation of kdenlive, and not the update to a new version, the simplest check would be to just uninstall kdenlive and see if the problem goes away.  

To remove all dependencies of kdenlive you may need to run
```
[...]$sudo apt-get autoremove
```

(I am not sure if synaptic can do that for you)

Thanks. I uninstalled kdenlive with no change. 

I would force the gstreamer package but I don't know exactly which gstreamer package to change. There are so many with gstreamer in the title.

---

### Post by jegerjensen on 2009-12-03
Have you tried playing with gstreamer-properties?

---

### Post by horseradish on 2009-12-03
> **jegerjensen said:**
> Have you tried playing with gstreamer-properties?

what is the name of the appropriate gstreamer file ?

---

### Post by Kevbert on 2009-12-03
If you know when the packages were updated you can look in the logfile to see what was changed. The logfile in question is /var/log/dpkg.log (or possibly dpkg.log.1). Using Nautilus filemanager just go to that directory and double click on dpkg.log to view it. Everything is time stamped. Once you have found what you think is the right package(s) run Synaptic to install or remove it (as Synaptic will handle any dependency issues).

---

### Post by Ric_NYC on 2009-12-03
> **horseradish said:**
> Is there a way to rollback ubuntu in the manner Windows does ? Either inkscape or kdenlive have altered my gstreamer and being able to rollback to how it was before would solve my problem. 

Rollback would seem more necessary for linux rather than windows.



I agree... Sometimes Linux is unforgiven... A rollback would solve mistakes any human being can make. A safe mode would be good too.

---

### Post by jegerjensen on 2009-12-03
> **horseradish said:**
> what is the name of the appropriate gstreamer file ?

Oh, I'm sorry, I meant that you could run the command
```
[...]$gstreamer-properties
```

This gives you a dialog with some settings to experiment with.

---

### Post by horseradish on 2009-12-03
> **Kevbert said:**
> If you know when the packages were updated you can look in the logfile to see what was changed. The logfile in question is /var/log/dpkg.log (or possibly dpkg.log.1). Using Nautilus filemanager just go to that directory and double click on dpkg.log to view it. Everything is time stamped. Once you have found what you think is the right package(s) run Synaptic to install or remove it (as Synaptic will handle any dependency issues).

thanks. how do I open nautilus ?

---

### Post by horseradish on 2009-12-03
> **jegerjensen said:**
> Oh, I'm sorry, I meant that you could run the command
```
[...]$gstreamer-properties
```

This gives you a dialog with some settings to experiment with.

I tried in terminal and got the same error I get with anything to do with gstreamer

*option parsing failed: Error re-scanning registry , child terminated by signal*

---

### Post by cgb on 2009-12-03
did a quick search and I believe this may be the same problem.  [http://ubuntuforums.org/showthread.php?p=8386553](http://ubuntuforums.org/showthread.php?p=8386553)

so basically try the below code which worked for them...
```
sudo apt-get remove frei0r-plugins
```

---

### Post by jegerjensen on 2009-12-03
I completely forgot to ask about error messages, this thread showed up on google:

[http://ubuntuforums.org/showthread.php?p=8386553](http://ubuntuforums.org/showthread.php?p=8386553)

It seems they solved it, have you tried what they did?

---

### Post by horseradish on 2009-12-03
> **cgb said:**
> did a quick search and I believe this may be the same problem.  [http://ubuntuforums.org/showthread.php?p=8386553](http://ubuntuforums.org/showthread.php?p=8386553)

so basically try the below code which worked for them...
```
sudo apt-get remove frei0r-plugins
```

It worked. thanks.

I has seen that thread already but was too cautious to try yesterday. Thanks again

---

### Post by Kevbert on 2009-12-03
> **horseradish said:**
> thanks. how do I open nautilus ?

Go to Places-Computer, Nautilus will open. Now double click on filesystem, double click on var...

---

