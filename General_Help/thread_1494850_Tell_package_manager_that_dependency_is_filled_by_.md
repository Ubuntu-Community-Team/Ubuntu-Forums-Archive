---
title: "Tell package manager that dependency is filled by other package"
date: 2010-05-27
forum: General Help
---

### Post by Ferrat on 2010-05-27
As the title suggests is there a way to "tell the package manager that dependency is filled by other package" I've built my own mplayer and codec packs and I know exactly what is in them but don't wanna build all the gstreamers, vlc ect pack that I really don't need to fix, thing is that for ex. my mplayer pack includes all the mplayer stuff in one pack while Ubuntu seperate it in to three packages I think mplayer, mencoder and one more I think, also I keep the SVN version to keep track of when I last updated while Ubuntu got their own version numbers in some cases. 

So in short how do I tell Synaptic or dpkg manager that the dependency is filled? as 99% of the time even the needed files are in the exact same place.. ?? 

Anyone? =)

Even better if I also could mark some packages as not maintained by the Ubuntu repo but by me instead..

---

### Post by ibuclaw on 2010-05-27
I take it you've got a source package tree for your custom version of mplayer?

If so, just alter the control file so that:
1) The package conflicts/replaces with the versions of gstreamer/etc in the Ubuntu Repository.
2) The package provides the package names.

ie:
```

Provides: package1, package2, package3
Conflicts: package1 (<< 1.0), package2 (<< 1.0), package3 (<< 1.0)

```
And rebuild it.

That should be enough to replace it. I think :)

Regards
Iain

---

### Post by Ferrat on 2010-05-27
> **ibuclaw said:**
> I take it you've got a source package tree for your custom version of mplayer?

If so, just alter the control file so that:
1) The package conflicts/replaces with the versions of gstreamer/etc in the Ubuntu Repository.
2) The package provides the package names.

ie:
```

Provides: package1, package2, package3
Replaces: package1 (<< 1.0), package2 (<< 1.0), package3 (<< 1.0)

```
And rebuild it.

Regards
Iain


Ah ok, thanks just what I was looking for :)

---

### Post by Ferrat on 2010-05-27
okey, problem, I use checkinstall and it has a Provides option but not a replaces option which seems to be needed for some? :/

---

### Post by ibuclaw on 2010-05-27
> **Ferrat said:**
> okey, problem, I use checkinstall and it has a Provides option but not a replaces option which seems to be needed for some? :/

Erm...

Having a look at [http://manpages.ubuntu.com/manpages/lucid/en/man8/checkinstall.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/checkinstall.8.html)
Try the option:
```
--review-control
```
Btw, I am only guessing here. Am not sure if it will have the desired effect you want...

---

### Post by Ferrat on 2010-05-27
> **ibuclaw said:**
> Erm...

Having a look at [http://manpages.ubuntu.com/manpages/lucid/en/man8/checkinstall.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/checkinstall.8.html)
Try the option:
```
--review-control
```
Btw, I am only guessing here. Am not sure if it will have the desired effect you want...

Great :) should be just what I need I hope

---

