---
title: "Linux for Development"
date: 2010-04-21
forum: General Help
---

### Post by mayapower on 2010-04-21
Hi,

It's been said that from a developer point of view, you should use and older version of distribution (as much as older as you can get and work with). The strongest reason behind this is glibc's forward-backward compatibility issue. I am a relatively new user of linux and finding this a bit frustrating rather then a solution.

My development mostly related to python, cython, api's and sdk's. Simple tests shows that if I am building on karmic 9.10, it's giving an error on 8.10 and asking for a higher glibc installed.

Using an older distribution  for development will solve this issue but is it the only way to do things? I have seen couple of article that says you can install an older version of glibc on a new system and compile your source against it but it's not advisable. There are chances that you might confuse the entire os and other programs may not work or in a distant possibility that you can also bring the entire system down.

I would like to know pointers from the developer's point of view that one should follow/remember, when working on linux based systems.

The bottom line is to create a single package that should be able to run on most of the distributions, rather then creating packages for each and every distro that you would like to support. I know that some where, some how your package will fail on some XYZ distro but still there must be some basic rules that one should follow.

If older version of a distro is the good starting point, then I don't mind using "hoary" or "breezy", but again I am not sure that I'll get some support in the forums. I recently tried with debain 4 "etch", and it was a bit of disappointment because distro is dead so does support and I am completely out of luck there. 


Prashant

---

### Post by Linuxforall on 2010-04-21
For this aspect, sticking to LTS is usually a good idea.

---

