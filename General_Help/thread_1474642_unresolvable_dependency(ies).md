---
title: "unresolvable dependency(ies)"
date: 2010-05-06
forum: General Help
---

### Post by Desim on 2010-05-06
Hi,

i'm using xubuntu 9.10 (2.6.31-20) 64 bits

In synaptic i wanted to install a game (lightyears) , but it returned an error saying 'Could not mark all packages for installation - The following packages have unresolvable dependencies. Make sure all required repos. are added and enabled in preferences.'
Of course, all needed repositories are checked in the settings...

Here is the concerned package: [COLOR=Blue]*python-pygame*[/COLOR]
I dug deeper to see why this package wouldn't install and found it had unresolved dependencies with: *[COLOR=Blue]python-numpy[/COLOR]*
Which in his turn told me he needed:
[I][COLOR=Blue]python-numpy:
 Depends: libblas3gf
 Depends: libgfortran3
 Depends: liblapack3gf
  [/COLOR][/I]All those were pointing to each other and finally to *[COLOR=Blue]libgfortran3[/COLOR]*
Which in turn told me something else:
[COLOR=Purple]"Depends: gcc-4.4-base (=4.4.1-4ubuntu8) but 4.4.1-4ubuntu9 is (to be) installed"[/COLOR]

Now, I thought of reinstalling this package hoping to solve the problem, but seeing how much packages depend on this guy, I prefered asking for some help first.

---

### Post by Desim on 2010-05-07
Up up, UP!

Seems like a tough question?

---

### Post by 101011010010 on 2010-05-07
Hello, Have you tried installing Build-Essential?

---

### Post by Desim on 2010-05-07
[COLOR=RoyalBlue][I]**Depends on resolvable dependencies and will not be installed**
build-essential:
 Depends: g++ but it is not going to be installed[/I][/COLOR]

I lol ... (do I?)

*sobs*
thanks anyways

It comes back to this [COLOR=Purple]gcc-4.4-base [COLOR=Black]dependency problem[/COLOR]
[/COLOR]

---

### Post by 101011010010 on 2010-05-07
O.o,lol missed that....Have you tried the Lucid repository? or here:> [http://packages.ubuntu.com/karmic/devel/build-essential](http://packages.ubuntu.com/karmic/devel/build-essential) You might also try changing the server in Software Sources.

---

### Post by Desim on 2010-05-07
> **101011010010 said:**
> O.o,lol missed that....Have you tried the Lucid repository? or here: You might also try changing the server in Software Sources.
Changing server didn't change a thing.

I downloaded the [COLOR=Purple]4.4.1-4ubuntu[COLOR=Black][COLOR=Purple]8[COLOR=Black] version[/COLOR][/COLOR][/COLOR][/COLOR]... BUT
Since i have [COLOR=Purple]gcc-4.4-base (=4.4.1-4ubuntu9 )[COLOR=Black] how can i get back to [/COLOR][/COLOR][COLOR=Purple]gcc-4.4-base (=4.4.1-4ubuntu[COLOR=Black][COLOR=Purple]8 )[/COLOR] without uninstalling everything that is depending on it ? (there are a LOT of packages depending on this guy...)
I cannot even reinstall this package...
[/COLOR][/COLOR]

---

