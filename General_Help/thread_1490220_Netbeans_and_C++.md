---
title: "Netbeans and C++"
date: 2010-05-22
forum: General Help
---

### Post by joshklewis on 2010-05-22
I have been searching through forums and tutorials for hours and just don't seem to get exactly what I need to do. I am hoping someone can help me.

I am trying to program with C++ using Netbeans. I want to be able to build a GUI, but have read I need GTK. I do not know how to get Gtk installed so that I can use it with Netbeans.

---

### Post by James78 on 2010-05-22
Install the GTK development packages, then include the header or cpp files into your program(s).

P.S. Isn't netbeans specifically written for Java? I would suggest you try Code::Blocks, which is specifically written for C++, but whichever you prefer. :)

---

### Post by joshklewis on 2010-05-22
You can get a plugin for Netbeans to code in C++. I have to learn Java for school as well, so I got Netbeans so that I can use the same IDE for both C++ and Java. I get that I need to get the GTK libraries, but I don't know how. I'm still rather new to Ubuntu and even more new to Netbeans.

---

### Post by James78 on 2010-05-22
Open up Synaptic package manager (System->Administration->Synaptic Package Manager), and install [libgtk2.0-dev]("http://packages.ubuntu.com/lucid/libgtk2.0-dev") and [libgnome2-dev]("http://packages.ubuntu.com/lucid/libdevel/libgnome2-dev").

A little more information on the header files can be found online with a Google search... An excellent book, I've heard that helps with Linux programming is Beginning Linux programming by Matthew/Stones (not sure if it helps with GTK though).

---

### Post by joshklewis on 2010-05-22
I downloaded the two libraries. I think I need to know the path to them. Have any idea where it saves the libraries to?

---

