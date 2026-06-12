---
title: "Netbeans and Sun Studio"
date: 2010-05-03
forum: General Help
---

### Post by joshklewis on 2010-05-03
I'm not sure if this is where I am suppose to put this question, so I apologize in advance just in case.

I am a beginner programmer and am looking for a C++ compiler for Ubuntu. I got Netbeans 6.8 but it did not come with a compiler for C++. I got Sun Studio 12 because I read it would work as a compiler for Netbeans. I am not sure what to do from here. Netbeans says that I do not have a valid C++ compiler and I'm not sure how to change the settings to make it recognize Sun Studio.

I found a couple tutorials but I did not understand what they were telling me to do.

---

### Post by QIII on 2010-05-03
The easiest thing to do would be to install g++ through Synaptic.

Just do a search for "g++" (no quotes, of course) and select the first one that is shown in the list, which should be g++.

All of the required dependencies should be installed along with it if you simply select g++.  (gcc will be included in the package.)

I'm not entirely sure if that will work with Sun Studio, but the g++ compiler is pretty generic, so I would think it should work.

---

