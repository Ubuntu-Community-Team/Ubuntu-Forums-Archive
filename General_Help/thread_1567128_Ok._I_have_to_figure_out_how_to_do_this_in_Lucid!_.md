---
title: "Ok. I have to figure out how to do this in Lucid! Please help with Gloobus."
date: 2010-09-03
forum: General Help
---

### Post by schwabdale on 2010-09-03
[http://www.omgubuntu.co.uk/2010/02/easily-install-nautilus-coverflow-in.html](http://www.omgubuntu.co.uk/2010/02/easily-install-nautilus-coverflow-in.html) 

I can't get it going. Please help

---

### Post by schwabdale on 2010-09-03
> **schwabdale said:**
> [http://www.omgubuntu.co.uk/2010/02/easily-install-nautilus-coverflow-in.html](http://www.omgubuntu.co.uk/2010/02/easily-install-nautilus-coverflow-in.html) 

I can't get it going. Please help


Any ideas?

---

### Post by schwabdale on 2010-09-03
bump

---

### Post by themusicalduck on 2010-09-03
You'll get much more help if you describe the problem better.

Tell us what you've done so far, what isn't working and if you have had any error messages.

---

### Post by schwabdale on 2010-09-03
> **themusicalduck said:**
> You'll get much more help if you describe the problem better.

Tell us what you've done so far, what isn't working and if you have had any error messages.

Sorry about that. I have installed Nautilus Elementary no problem. 
I also installed Gloobus preview no problem. I somehow found a .deb package named
gloobus_0.4_i386..... I think this is the coverflow part. When I run this package I get an error ( Error: Dependency is not satisfiable: libclutter-0.9-0 )

I can't find anywhere in Google to install Gloobus Coverflow for Nautilus.

---

### Post by themusicalduck on 2010-09-05
Try running these commands in a terminal ```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
sudo apt-get update
sudo apt-get install covergloobus
```

Hopefully that will install the latest version for you.

---

### Post by schwabdale on 2010-09-07
> **themusicalduck said:**
> Try running these commands in a terminal ```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
sudo apt-get update
sudo apt-get install covergloobus
```Hopefully that will install the latest version for you.

It says it installed... but how do I see the coverflow in Nautilus?

---

### Post by themusicalduck on 2010-09-07
According to the article you linked -

> Open up a folder (any one) and either hit CTRL+4 or enable the coverflow effect via View > Clutter View. If you click on the cover flow itself you can then slide through items using your mouse scroll wheel or left/right keyboard keys.

If that isn't working, then it's hard to guess. Check you're using Nautilus Elementary (it'd probably tell you under Help, About or something similar). You'd also need to restart Nautilus after having installed it (killall nautilus) or just restart the PC.

---

### Post by ammonkey on 2010-09-08
coverflow in nautilus-elementary worked under karmic, then the interface changed in lucid and this functionality disappeared. It is now implemented back again in maverick. (sorry but it's not available in lucid).

[http://ammonkey.posterous.com/reviving-old-clutterview-code-maverick-pkg](http://ammonkey.posterous.com/reviving-old-clutterview-code-maverick-pkg)

---

