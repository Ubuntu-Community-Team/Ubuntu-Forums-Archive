---
title: "Burn VCD in Linux"
date: 2006-01-23
forum: General Help
---

### Post by Prudentissimus on 2006-01-23
I have *.mpg files,...

And I have GnomeBaker,


How do I burn mpg to VCD format...

---

### Post by Briquet on 2006-01-23
Simple, install vcdimager

sudo apt-get install vcdimager

then use it this way in the terminal: 

vcdimager -t vcd2 -c nameofthefile.cue -b nameofthefile.bin nameofthefile.mpg

Finally burn as an image one of the files generated (I don't remember if was the .cue or the .bin)

Done

---

### Post by RikoW on 2006-01-24
if you create the .bin and .cue file as Briquet suggested, you can fire up k3b as your burning tool and select "Burn CD Image". it will then list in the image file selection the correct image file (I think, it uses the .cue actually) and you can create your VCD.

Have fun,

           Riko

---

### Post by Lem on 2006-01-24
K3b also has a 'create video cd' function. It's a KDE app, but works great in gnome and easily the best burning app out there. Might be easier if you don't like delving into terminal to do everyday tasks.

---

### Post by gustysoft on 2007-09-25
Hi my name is Gustavo. With vcdimager can convert one files, but I wanna convert 100 files mpg to vcd (in this case to dvd video). How do I have to do to convert and burn 100 files in the same time?
Thx.
Gus.
Sorry for my English, I'm learning. Bye

---

### Post by steve8track on 2008-02-02
It appears that **K3b** lets you drag and drop all .mpg file to add them to a Video CD project or other types of projects.  If you can't use K3b, you could write a **shell script** to iterate through the files in a a folder and run the tool others mentioned above.  If you need to convert the files to mpg from something like flv (like videos from youtube), you can use **ffmpeg**, which is a command line utility, which can also be scripted to convert all of the files.

---

