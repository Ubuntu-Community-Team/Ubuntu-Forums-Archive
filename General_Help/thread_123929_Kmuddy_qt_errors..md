---
title: "Kmuddy qt errors."
date: 2006-01-31
forum: General Help
---

### Post by h4ck3r on 2006-01-31
Ok, I want to install kmuddy (kmuddy.net) on ubuntu 5.10, but when I do ./configure I get this qt error...

checking for Qt... configure: error: Qt (>= Qt 3.1.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

I have libqt3-mt among lots of others installed so what is the problem?

---

### Post by mlomker on 2006-01-31
You probably need **kde-devel**, which is a large package.

---

### Post by h4ck3r on 2006-01-31
I have that package also drat... I so want kmuddy. Anyone else have any ideas?

---

### Post by nrwilk on 2006-01-31
I recently found the answer on the kmuddy forums.

when running the configure command before compiling, use this command, which works for me:

```

./configure --with-qt-dir=/usr/share/qt3 --with-qt-includes=/usr/include/qt3 --with-qt-libraries=/usr/lib/qt3

```

basically you have to specify the location of the directories where you system has it's qt header libraries.

after that just do the usual:
```

make
sudo make install

```


Let me know if you get weirdness with the ANSI color in the output window.  In my build when a line is output to my screen with multiple colors in the same line, the client puts like 40 spaces between the different colored text.  I know this to be a property of the client and not the MUD itself because I visited the mud with several other clients, and Kmuddy did this with several different MUDs.  I haven't found any fixes, or even a mention of this problem on the Kmuddy forums.  Let me know if you experience it.  If not, maybe you could send me a deb?

---

### Post by h4ck3r on 2006-01-31
Thank you so much I love kmuddy so much it is the best \\:D/  way better then anything else. I will let you know if I have some problems.

---

### Post by h4ck3r on 2006-01-31
Colors seem to work finge :)

---

### Post by nrwilk on 2006-01-31
I'm glad you got it working!

I wish my client would handle colors without problem, but 0.7 and also the 0.8beta have the same problem for me.  sucky.

---

### Post by nrwilk on 2006-02-03
After talking to the Author of Kmuddy, it seems that it's an issue with the way some fonts represent their own character widths.  Changing fonts has cleared up the color problem for me.  for more info about this see what he said below:

[QUOTE=Tomas Mecir]KMuddy displays the text in chunks, with 
each chunk being composed of text of one color. It computes the position of 
further chunks based on font's information about width of each character. If 
this fails to work properly, you end up with this. Sounds to me like some 
problem with font's metrics - another font may work correctly.
...
You need a non-proportional font. Some versions of the font library / fonts 
seem to propagate themselves wrongly, leading to proportional fonts being 
shown in the list, leading to problems like this.[/QUOTE]

My view is that any info that can be useful should be easily available, so I like to post anything that may be of use.

Have fun mudding!

---

