---
title: "make: error: X11/Xlib.h No such file or directory"
date: 2009-12-03
forum: General Help
---

### Post by Fizz44 on 2009-12-03
I'm running Ubuntu 8.04 LTS and I love it!  I have been working with Octave-3.0.0, which is the newest rev I can get with Synaptic.  I ran into something that was not working that I really want, so I went to mailto:help-octave@octave.org for help.  The developer replied:

It seems to work correctly for me with the current stable version of
Octave, 3.2.3.  I recommend upgrading.

I tried upgrading, from [www.octave.org]("http://www.octave.org"), taking all defaults, but it failed.  "config.log" contained a great many instances of:
  configure: failed program was:
  | /* confdefs.h.  */
each was proceeded by a different error or exit code, for examples:

configure:7207: checking for X
configure:7377: gcc -o conftest -g -O2   conftest.c -lX11  >&5
conftest.c:28:22: error: X11/Xlib.h: No such file or directory
configure:7383: $? = 1
configure: failed program was:
| /* confdefs.h.  */

configure:10463: checking glpk/glpk.h presence
configure:10478: gcc -E  conftest.c
conftest.c:38:23: error: glpk/glpk.h: No such file or directory
configure:10484: $? = 1
configure: failed program was:
| /* confdefs.h.  */

locate {Xlib.h,glpk.h} turned up neither.
Synaptic seems to show that my X-environment is from "libx11-6"; it's description mentions "...otherwise known as 'Xlib'."

Is there a disconnect here?  Is there a simple way to reconnect?

Is there a better way to upgrade to a newer version of a package than what Synaptic offers (with all software sources opened).

I'm stuck.

---

### Post by lloyd_b on 2009-12-04
You're missing the development packages for a couple of dependencies.  Specifically, you need to install the packages "libx11-dev" and "libglpk0-dev".

I wouldn't be surprised if you're missing a few other dependencies as well, so I'd suggest running "sudo apt-get build-dep octave3.0" in a terminal window.  This will get all the dependencies required to compile Octave 3.0, which hopefully be all that are required for 3.2.3 as well.

Lloyd B.

---

### Post by Fizz44 on 2009-12-05
YES!  Thank you Lloyd.

Sordid details:
I tried sudo apt-get build-dep octave3.0; it failed, but told me that
libcurl4-dev is virtual package provided by libcurl4-gnutls-dev and that I should 
select one to install ....
So, I went back to Synaptic, found libcurl4-gnutls-dev and installed it, and repeated
sudo apt-get build-dep octave3.0.  This time it spit out a list of dependencies.  None of
them looked like X, so I bailed out, didn't install them.  Instead, I ran updatedb, then
locate Xlib; this time it found: /usr/include/X11/Xlib.h.  This's what I needed, but I don't really know where it came from; was it libcurl4-gnutls-dev?  That's counter intuitive.
I had previously tried installing libx11-dev, and that didn't help.

Anyway, I now have Octave3.2.3 running on my Ubuntu8.04 LTS Lenovo T61 notebook, and
I'm a happy camper.  It doesn't have the sparse matrix functions and some other stuff I 
don't need now, but if I need any of that later, I should be able to install it.

Outstanding!
:D

---

