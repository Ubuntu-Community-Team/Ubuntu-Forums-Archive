---
title: "How to find dependencies that are not in repos?"
date: 2009-07-29
forum: General Help
---

### Post by uberlube on 2009-07-29
This is something that has been making me frustrated for a long time but I always ended up just "living with" and older version of a program. But in this case I cant live with an older version of sauerbraten (ie the one that ha been sitting in the repos FOREVER and isnt playable) because u cannot connect to any server without the newest protocol. So i downloaded the source and have looked at all the readmes to get info on all the dependencies needed to compile and this is what it asks for.

```
Clients will need the following dynamic link libraries present:
* libGL (OpenGL)
* SDL (>= 1.2.10)
* SDL_image
* SDL_mixer
* libpng
* libjpeg
* zlib
```

So I hit up the repos just to find that some of these are not in there as described. My question, is where do I find these elusive dependencies and how do i properly add them into my install? What is the best way of going about this?

---

### Post by bodhi.zazen on 2009-07-29
First enable all your repositories (Universe and multiverse)

Then```
sudo apt-get update
```And search the repositories if needed :

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zlib&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=zlib&searchon=name&subword=1&version=all&release=all)

If that fails, google and find the Home page.

---

