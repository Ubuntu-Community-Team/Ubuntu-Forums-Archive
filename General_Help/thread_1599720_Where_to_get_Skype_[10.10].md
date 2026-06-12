---
title: "Where to get Skype? [10.10]"
date: 2010-10-18
forum: General Help
---

### Post by XEtedBear on 2010-10-18
Apologies if this is in the wrong sub-Forum

During the install of 10.10 yesterday, while watching the slide show, I noticed the claim that Skype is supported under 10.10. But when I searched for the skype package in the Software Centre I don't find it. I find a reference to something called a Skype API wrapper for python - which sounds like the sort of thing you find lying the ground outside the reptile house at your local zoo after a successful attack on a hamburger-eating visitor. Surely that can't be it?

Where do I find the Skype package?

---

### Post by Bradtek on 2010-10-18
Have you checked all the boxes in the Software sources, Universe, Multiverse etc ?

Ubuntu Software Center | Edit | Software Sources

---

### Post by XEtedBear on 2010-10-18
> **Bradtek said:**
> Have you checked all the boxes in the Software sources, Universe, Multiverse etc ?

Ubuntu Software Center | Edit | Software Sources

Hmm, that's most helpful - thanks. I have to confess I never even saw the meu items (File, Edit ...) because my eye went directly to the panel of Categories and then to the search box.

However, following your tip, I found that all the (apparently, to me) relevant boxes were already ticked. And the search still doesn't find a Skype package.

Maybe I just imagined that there is a Skype for Linux....

---

### Post by plucky on 2010-10-18
Try enabling the **Partner** repositories under the "Other Software" tab in Software Sources and then "Reload" to update the index file.

---

### Post by lonniehenry on 2010-10-18
Go to the Skype website and search around.  There are debs for linux and linux 64 bit for install.

---

### Post by mister_playboy on 2010-10-18
> **lonniehenry said:**
> Go to the Skype website and search around.  There are debs for linux and linux 64 bit for install.

Specifically: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/)

---

### Post by HermanAB on 2010-10-18
Howdy,

When all else fails, you can download the 'static' version from the Skype web site.  It is a little larger download, but it doesn't have dependencies on shared libraries, so it just works.

---

### Post by XEtedBear on 2010-10-18
> **plucky said:**
> Try enabling the **Partner** repositories under the "Other Software" tab in Software Sources and then "Reload" to update the index file.

This repository was already enabled; I can find no 'reload' option in any menu in the Software Centre application.

---

### Post by plucky on 2010-10-18
> **XEtedBear said:**
> This repository was already enabled; I can find no 'reload' option in any menu in the Software Centre application.

Open a terminal and ```
sudo apt-get update
sudo apt-get install skype
```

If that doesn't work,post the output of ```
cat /etc/apt/sources.list
```

Good Luck

---

### Post by 98cwitr on 2010-10-18
I just got the .deb file from skype's website
[http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)

---

### Post by XEtedBear on 2010-10-20
> **plucky said:**
> Open a terminal and ```
sudo apt-get update
sudo apt-get install skype
```


Good Luck

OK, that worked, thanks. But I don't understand why Skype is not available in 10.10 'out of the box' - by which I mean on the installation DVD.

---

