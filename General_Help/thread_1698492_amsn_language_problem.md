---
title: "amsn language problem"
date: 2011-03-02
forum: General Help
---

### Post by jolian ramos on 2011-03-02
when i try to use amsn and write other language beside english like arabic i find that letters are written but in reversed way so can any one help me please i provide a photo for you 
thanks guys  


[[IMG]http://img88.imageshack.us/img88/1238/screenshotyw.jpg[/IMG]]("http://img88.imageshack.us/i/screenshotyw.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by regala on 2011-03-02
> **jolian ramos said:**
> when i try to use amsn and write other language beside english like arabic i find that letters are written but in reversed way so can any one help me please i provide a photo for you 
thanks guys  


well, amsn wasn't developed with bidirectional support in mind, or tcl/tk libraries don't provide that kind of support (which I don't believe). in any case, no "fix" is straightforward: support has to be added to the amsn code (or worst case scenario: in the tcl/tk libraries).

but bear in mind that it's a display glitch: whoever is sent this right-to-left text displayed form left to right on your screen, will read it from right-to-left in her client, if bidir is implemented in that client.

br,

Mathieu

---

### Post by jolian ramos on 2011-03-02
> **regala said:**
> well, amsn wasn't developed with bidirectional support in mind, or tcl/tk libraries don't provide that kind of support (which I don't believe). in any case, no "fix" is straightforward: support has to be added to the amsn code (or worst case scenario: in the tcl/tk libraries).

but bear in mind that it's a display glitch: whoever is sent this right-to-left text displayed form left to right on your screen, will read it from right-to-left in her client, if bidir is implemented in that client.

br,

Mathieu
  i don't understand sir do you mean that there is no solution for this ?!!!! i don't know about tcl/tk libraries

---

### Post by jolian ramos on 2011-03-03
> **regala said:**
> well, amsn wasn't developed with bidirectional support in mind, or tcl/tk libraries don't provide that kind of support (which I don't believe). in any case, no "fix" is straightforward: support has to be added to the amsn code (or worst case scenario: in the tcl/tk libraries).

but bear in mind that it's a display glitch: whoever is sent this right-to-left text displayed form left to right on your screen, will read it from right-to-left in her client, if bidir is implemented in that client.

br,

Mathieu
[SIZE=2]  i don't understand sir do you mean that there is no solution for this ?!!!! i don't know about tcl/tk libraries[/SIZE]

---

### Post by jolian ramos on 2011-03-04
[SIZE=2]  i don't understand sir do you mean that there is no solution for this ?!!!! i don't know about tcl/tk libraries

please any kind of help this is urgent for me as i am not expert about ubuntu i just turned to use it since few days instead of windows 7
[/SIZE]

---

