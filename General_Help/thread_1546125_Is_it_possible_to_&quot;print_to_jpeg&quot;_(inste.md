---
title: "Is it possible to &quot;print to jpeg&quot; (instead &quot;print to PDF&quot;)?"
date: 2010-08-04
forum: General Help
---

### Post by ruipedroca on 2010-08-04
Hi,

Is it possible to "print to jpeg" (instead "print to PDF")?

---

### Post by WorMzy on 2010-08-04
Not as far as I know. You can, however, run a terminal command to convert a variety of formats to an image, using imagemagick. 

[http://amath.colorado.edu/computing/software/man/convert.html](http://amath.colorado.edu/computing/software/man/convert.html)

```
convert <inputfile> <outputfile>
```

---

### Post by SoFl W on 2010-08-04
Try printing to the pdf and then try
```
convert filename.pdf filename.jpg
```at least try 
```
convert --help
```
EDIT:  I tried the PDF to JPG convert, it works.

---

### Post by Freelance Physicist on 2010-08-05
There might be a better/easier way.  What exactly are you trying to convert into a jpeg?

---

### Post by ruipedroca on 2010-08-05
> **Freelance Physicist said:**
> There might be a better/easier way.  What exactly are you trying to convert into a jpeg?

I'm particularly interested in exporting JPG from Openoffice Calc :roll:
That would be great!:)

---

### Post by Freelance Physicist on 2010-08-05
I think it would be easier to take a screenshot of the spreadsheet you want to turn into a jpeg.  If all the cells you want to print are visible on screen, you can just push the PrintScreen button on your keyboard and save the resulting picture (it will be a png isntead of a jpeg, if that matters to you).  You can then use a program like GIMP to crop the picture to the parts you need.

Here's something I just discovered: if you open up a terminal (Applications->Accessories->Terminal) and type
```
gnome-screenshot --interactive
```
a box will appear with the option to select which part of the screen to save as a picture.  This should save you some time in cropping.

---

### Post by ruipedroca on 2010-08-05
> **SoFl W said:**
> Try printing to the pdf and then try
```
convert filename.pdf filename.jpg
```at least try 
```
convert --help
```
EDIT:  I tried the PDF to JPG convert, it works.
This is great!:)

---

### Post by ruipedroca on 2010-08-05
> **Freelance Physicist said:**
> 
```
gnome-screenshot --interactive
```
a box will appear with the option to select which part of the screen to save as a picture.  This should save you some time in cropping.
Very good tip! Thanks for sharing:)

---

### Post by SoFl W on 2010-08-06
> **Freelance Physicist said:**
> ```
gnome-screenshot --interactive
```
Nice, I didn't know about the selection tool, I know "Print Screen" will get the whole screen and "ALT-Print Screen" will get the current window, but I didn't know about the selection tool.  Is there a keyboard shortcut?

> **ruipedroca said:**
> This is great!:)
Give credut to WorMzy also, he pointed it out!  :D

---

### Post by AlphaLexman on 2010-08-06
Technically, .png reproduces text images better than .jpg so you should consider this different format if possible.

---

### Post by Freelance Physicist on 2010-08-06
> **SoFl W said:**
> Nice, I didn't know about the selection tool, I know "Print Screen" will get the whole screen and "ALT-Print Screen" will get the current window, but I didn't know about the selection tool.  Is there a keyboard shortcut?
No, but you can create one.  Go to System->Preferences->Keyboard shortcuts and click on Add, then fill in the boxes.  For Name, I use "Take a screenshot with options" and for Command, use
```
gnome-screenshot --interactive
```
After clicking Apply, scroll to the bottom of the list and click on Disabled to assign a shortcut key (I used Ctrl+Shift+PrintScreen).

---

### Post by ruipedroca on 2010-08-06
> **SoFl W said:**
> Nice, I didn't know about the selection tool, I know "Print Screen" will get the whole screen and "ALT-Print Screen" will get the current window, but I didn't know about the selection tool.  Is there a keyboard shortcut?

Give credut to WorMzy also, he pointed it out!  :D
You're right!:)
Thanks WorMzy!:p

---

### Post by l0co on 2011-09-26
> **SoFl W said:**
> Try printing to the pdf and then try
```
convert filename.pdf filename.jpg
```

Sometimes is also useful to convert pdf into a **single** image file. For this use:

```
convert -append filename.pdf filename.jpg
```

---

