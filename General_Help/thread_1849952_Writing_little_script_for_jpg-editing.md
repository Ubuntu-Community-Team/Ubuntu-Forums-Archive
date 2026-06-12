---
title: "Writing little script for jpg-editing"
date: 2011-09-25
forum: General Help
---

### Post by Boulemans on 2011-09-25
Hi all,

I'm trying to write a script for the following: I have a collection of 200 jpg files. I want to 

1) turn every image 180° (since there are all upside down)
2) form them into one pdf file (all scans are in the right order, like: scan001 scan002, ...)

Could someone help me with this? I'm trying to do this with a script, but I don't have enough knowledge of scripting.

Boulemans

---

### Post by MG&amp;TL on 2011-09-25
You might have a look at Phatch:

[http://photobatch.stani.be/]("http://photobatch.stani.be/")

It didn't do what I wanted it to do, but what it did was a LOT.

---

### Post by nothingspecial on 2011-09-25
First stop imagemagick

```
convert -rotate 180 *
```

I have to admit I don't know how to make the results into a pdf.

:D

---

### Post by SecretCode on 2011-09-25
Second stop also imagemagick!

```
convert *.jpg output.pdf
```

But read the man page carefully - I believe you need to set options to control the quality.

Not tested!

---

### Post by ajgreeny on 2011-09-25
> **SecretCode said:**
> Second stop also imagemagick!

```
convert *.jpg output.pdf
```But read the man page carefully - I believe you need to set options to control the quality.

Not tested!
I can confirm that it works well, but I do find the man page for convert so difficult to decipher that I am not at all sure how you set the quality of pdf output.

Anyone else know?

---

### Post by Boulemans on 2011-09-26
I've tried to rotate them with imagemagick, and succeded, but came with the following problem:

If i want to rotate all of the images (over 200), after a long time waiting he eventually says that his memory is full and aborts the procedure, resulting in no output files for any of the input files.

My conclusion from this is that he doesn't make a hard-safe of the new images directly after rotating, but saves it temporary in his RAM memory, until he rotated all the images, and then wants to save them on the hard drive. After some images, his RAM memory gets full and results in a error message.

Tough I've already rotated them in groups of 20, I wander if it would be possible (python script?) to write a loop so he rotates, saves on hard drive, rotates next image, saves on hard drive, and so on? I just want to learn here :-)

---

### Post by Slim Odds on 2011-09-26
```

for f in *.jpg; do
    convert -rotate 180 "$f"
done

```

---

