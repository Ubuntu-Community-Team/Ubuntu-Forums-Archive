---
title: "Flashplugin-nonfree broken help!"
date: 2009-11-16
forum: General Help
---

### Post by polardude1983 on 2009-11-16
Ok so i got a red icon on the top right of my screen saying

An error occurred, pleas run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0' THis usually means your isntalled packages have unmet dependencies.

So I went to the Synaptic Package manager did custom filters and found the broken package. 

which is flashplugin-nonfree 9.0.124.0ubuntu2 

I hit FIx Broken packages then i hit apply Then this message comes up

E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

I can't install anything from the ubuntu software center anymore, i guess not until i fix this :/ plz helps

---

### Post by t0p on 2009-11-16
You weren't very clear on this point: you said you can't install anything with the software center - but what about using synaptic? Or apt-get on the command-line?

I suggest trying to (un)install the plugin through those means, if you can.

---

### Post by polardude1983 on 2009-11-16
Newb ubuntu/linux person here.

trying to be clear

As said i tried to upgrade/install the flashplugin-nonfree by hitting apply and then it said. 

E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

which wasn't i trying to reinstall it when i hit apply after i hit fix broken packages?

---

### Post by Monotoko on 2009-11-16
type into the terminal

(Applications -> Accessories -> Terminal)

```
sudo apt-get remove --purge flashplugin-nonfree
```

Then reinstall it :)

---

### Post by polardude1983 on 2009-11-16
I ran that and this is what i got from the terminal

```
dpkg: error processing flashplugin-nonfree (--purge):
Package is in a very bad inconsistent state - you should
reinstall it before reattempting a removal.
Errors were encountered while processing:
flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by polardude1983 on 2009-11-16
I edited the /var/lib/dpkg/status

took out the flashplugin-nonfree and then fixed a package cause i edited that and bam working again. now i can isntall things again

---

### Post by gwm on 2009-11-17
I had a similar problem. It turned out to be that I was missing the adobe repository in my sources.list file. Here is where I got the fix. **[http://ubuntuforums.org/showthread.php?t=1328128](http://ubuntuforums.org/showthread.php?t=1328128)**

---

