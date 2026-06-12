---
title: "Exporting Packages from Ubuntu to install on another Ubuntu (like FEBE for Firefox)"
date: 2010-04-14
forum: General Help
---

### Post by Milkman08 on 2010-04-14
Hi

Can I export software installed on ubuntu to deb package files and install them on another system , just like Kyrix , or as FEBE does it for Firefox?

I think it's not possible ... ,but, wanted to make sure :)

Thanks

---

### Post by nothingspecial on 2010-04-14
You can find debs of anything you have installed (with apt, software center or synaptic) in ```
/var/cache/apt/archives
```

Simply copy them across

You can also find debs of all ubuntu packages [[COLOR="Magenta"]here[/COLOR]]("http://packages.ubuntu.com/")

---

### Post by dearingj on 2010-04-14
> **nothingspecial said:**
> You can find debs of anything you have installed in ```
/var/cache/apt/archives
```

Simply copy them across

That's assuming the cache hasn't been cleared. If the cache has been cleared, you can use Synaptic to generate a package download script: just open Synaptic, mark the packages you want for (re)installation, then open the File menu and choose to generate the script. Run this script on any Internet-connected Linux computer to download the packages.

---

### Post by Milkman08 on 2010-04-14
> **dearingj said:**
> That's assuming the cache hasn't been cleared. If the cache has been cleared, you can use Synaptic to generate a package download script: just open Synaptic, mark the packages you want for (re)installation, then open the File menu and choose to generate the script. Run this script on any Internet-connected Linux computer to download the packages.

So you mean there's no way to get it offile from the system and I have to download packages again?
There's no way I can export the already installed ones on my system?

---

### Post by nothingspecial on 2010-04-14
Type ```
ls /var/cache/apt/archives
```

and post the output here.

Of course if the packages you want to install have dependencies then they will have to be copied and installed too.

But if you haven`t cleared your cache, they will be there also.

---

### Post by Milkman08 on 2010-04-14
Yeah , I saw the content of that folder and some debs were still there.
Thanks the info was useful to me, but still, you can't get ALL of the packages you installed right?
Just the one's that remained in cache ...
So, I have to *download* the rest of the packages I installed.

Could anyone give me a clear answer about my question? can I export packages from the system, as FEBE extenetion rebuilds .xpi files from browser data, or not?

---

### Post by lovinglinux on 2010-04-15
> **Milkman08 said:**
> Yeah , I saw the content of that folder and some debs were still there.
Thanks the info was useful to me, but still, you can't get ALL of the packages you installed right?
Just the one's that remained in cache ...
So, I have to *download* the rest of the packages I installed.

Could anyone give me a clear answer about my question? can I export packages from the system, as FEBE extenetion rebuilds .xpi files from browser data, or not?

I don't know i that is possible. What I do is to download and install them like dearingj suggested, but I have developed a Firefox extension to do that, called [UMarks](http://lovinglinux.megabyet.net/?page_id=534). 

Perhaps I could try to implement such feature. Hmmm, this could be fun :)

---

### Post by Milkman08 on 2010-04-15
> I don't know i that is possible. What I do is to download and install them like dearingj suggested, but I have developed a Firefox extension to do that, called UMarks. 
Thanks :) I'll definatly try it, altough as you said, it does the same thing that dearingj suggested, only automatically ...
> Perhaps I could try to implement such feature. Hmmm, this could be fun :)
It'll be double super freakin awesome (!) if you do that :D wow, just think how you make life for Ubuntu user's easier ...

Just, if you could make a version that works with firefox versions 3.X.XX ...

---

### Post by lovinglinux on 2010-04-15
> **Milkman08 said:**
> Thanks :) I'll definatly try it, altough as you said, it does the same thing that dearingj suggested, only automatically ...

It'll be double super freakin awesome (!) if you do that :D wow, just think how you make life for Ubuntu user's easier ...

Just, if you could make a version that works with firefox versions 3.X.XX ...

Mozilla will soon drop the support for Firefox 3.0.x, so I don't have plans support it either. Besides, Firefox 3.5 introduced some extension API changes, that are incompatible with 3.0.x. The extension actually works on Firefox 3.0, but with limitations. You cannot see the list of installed packages, but you can create backups, export, import and download/install the packages.

If you want full support, see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It explains how to get the latest Firefox without upgrading Ubuntu.

I will need some time to do this, but if you install the extension you will get updates through Firefox add-on manager. You could also subscribe to [this thread](http://ubuntuforums.org/showthread.php?t=1216679), where I post info about new releases.

---

### Post by lovinglinux on 2010-04-17
> **Milkman08 said:**
> It'll be double super freakin awesome (!) if you do that :D wow, just think how you make life for Ubuntu user's easier ...

Just a heads up....

The new version is ready. Now is it possible to download the packages to the extension cache, install them from the cache or export as archive. 

The exported package archive carries all deb files and can be imported back to Umarks, then installed. 

I'm really excited with this new version. I'm not going to release it until I perform more tests. It is working fine with a couple of packages, but I want to test it with a complete new system. This is going to be fun.

---

### Post by lovinglinux on 2010-04-20
The extension is ready and can be downloaded from my blog or from Mozilla web site, although it will take a couple of days before the new version shows up on Mozilla site.

See [http://umarks-extension.blogspot.com](http://umarks-extension.blogspot.com)

---

