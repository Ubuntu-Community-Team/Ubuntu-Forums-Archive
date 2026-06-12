---
title: "Program GUI Frontend"
date: 2009-09-03
forum: General Help
---

### Post by Psycho.mario on 2009-09-03
How would i go about writing a GUI front-end for programs like dd, ffmpeg, nmap or cat? Something where you choose an option from a drop down box, which corresponds to a command line arguament, so you can easily create long commands.

I know there are frontends for nmap and ffmpeg, but i want to learn and create my own.

Thanks

---

### Post by HermanAB on 2009-09-03
Perl and Glade3 is the answer.

I have written lots of little wizards over the years and that is the way to do it.

Here are some examples:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

### Post by Psycho.mario on 2009-09-04
I might just use zenity and a bash script. I think perl and glade is a little to much to learn at the moment, im going back to school to start my GCSEs on tuesday.

---

### Post by tlacuache on 2009-09-04
Using Free Pascal and Lazarus you can create GUI applications that run on a variety of platforms (Windows, Linux, OS X, etc.). Free Pascal's "TProcess" object makes it trivial to execute command-line utilities and pipe input and output to and from these programs.

[http://lazarus.freepascal.org/](http://lazarus.freepascal.org/)

---

### Post by Psycho.mario on 2009-09-04
that still means i have to learn something. Is there no GUI to make a GUI? If you get what i mean?

---

