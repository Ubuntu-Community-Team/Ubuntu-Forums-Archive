---
title: "Is ther any lib need before compiling"
date: 2009-11-20
forum: General Help
---

### Post by r.mariappan on 2009-11-20
Hi everyone.. 
I read many places that i can compile the source package using 
./configure
make
make install
But i never crossed even the first step. I had been trying to compile atleast one package. But i never succeeded in that. i have been trying that for months. Every time i got some error. For that itself i usually search and download only binary packages. Pleas tell me how to compile. Do I need to install any other thing(library files) before compiling. I remembered i installed make for this. But eventhough i never succeed. Any one help me.......

---

### Post by Giblet5 on 2009-11-20
First, install the build-essential package if you haven't already.

Now, when you run ./configure on a source package, it will complain if something is missing eg, "libcurl".

So open Synaptic and click the "Search" button. Enter "libcurl".

In the displayed list of matching packages, scroll down to the packages beginning with "libcurl" and look for a "-dev" package. On 9.10, that'll be "libcurl4-dev" mark it for install and click Apply. Leave Synaptic open.

Run ./configure again. You might get another error, but it won't be libcurl... See how this works?

---

