---
title: "update problem"
date: 2012-02-26
forum: General Help
---

### Post by drofart on 2012-02-26
Hello friends,
    yesterday i cancel my update in middle & today when i tried to update i got an error msg(screen shot in attachment)  . Any help is appreciated .

thnx.

---

### Post by audiomick on 2012-02-26
It might make it easier to help with that if you try again, and click on "details" in that window in your screenshot, and post a screenshot of the details so that people can see more of what is going on.

---

### Post by drofart on 2012-02-26
> **audiomick said:**
> It might make it easier to help with that if you try again, and click on "details" in that window in your screenshot, and post a screenshot of the details so that people can see more of what is going on.

it says ```
firefox firefox-globalmenu firefox-gnome-support firefox-locale-en libpng12-0 libvorbis0a libvorbisenc2 libvorbisfile3 linux-headers-2.6.38-13 linux-headers-2.6.38-13-generic linux-image-2.6.38-13-generic linux-libc-dev thunderbird thunderbird-globalmenu update-manager update-manager-core"
```

---

### Post by audiomick on 2012-02-27
I'm guessing here, but two things occur.

Have you got any PPA's installed? It is complaing about lacking authentification, which indicates that one or more PGP keys are missing.
If you have any package sources installed other than the standard ones, you could try disabling them.

The other thing is, I notice that the update manager is listed in the error output. Perhaps it got broken when you stopped the update. I do not know if this is safe or not, but I would probably try re-installing that with synaptic to see if that helps. As I said, that is a guess and not a definite fix.

---

### Post by raja.genupula on 2012-02-27
open your terminal and type 
```
sudo apt-get update
```

report any errors , if no then do 
```
sudo apt-get upgrade

```
let us know what you got .

---

### Post by drofart on 2012-02-27
> **raja.genupula said:**
> open your terminal and type 
```
sudo apt-get update
```report any errors , if no then do 
```
sudo apt-get upgrade

```let us know what you got .
Hello raja, it worked like a charm ! Did i tell i love all  ubuntu guys!

Thank you everyone for their valuable opinion. :)

---

