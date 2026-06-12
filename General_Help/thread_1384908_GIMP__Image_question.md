---
title: "GIMP / Image question"
date: 2010-01-18
forum: General Help
---

### Post by jimmyUT on 2010-01-18
I have an image that I am trying to manipulate using GIMP, but I can't figure it out.  Hopefully someone can help me out and let me know if this can be done within Ubuntu somehow.

Image is below and I can have it in any format that Xsane scanner will save

What I am trying to do is change everything that is black to red, while keeping the background white.

Any ideas if this can be done with GIMP or any other programs within Karmic.

Thanks for you help.

---

### Post by todak on 2010-01-19
Open your image in GIMP. In the image window go to **Select >By Color**. Choose the color you wish to change. Then click on the Bucket Fill icon in the toolbox window. Next click on the Foreground color patch (the black rectangle on top of the white rectangle). Choose the shade of red you desire. Then select **Fill Whole Area** in the **Bucket Fill** window. Click on the area that you wish to be red. Then go to Select >None. Your Black areas will then be red.

---

### Post by jimmyUT on 2010-01-19
Did not work.  It made the whole picture gray for some reason.

Do I need to save the file in a specific format first?

---

### Post by todak on 2010-01-19
> **jimmyUT said:**
> 
Do I need to save the file in a specific format first?

Use **File >Create >Xsane** to acquire an image from your scanner. Then edit it as I outlined above, then save it as whatever you wish. Or you can scan it with Xsane first and then save it as an image file such as JPG, PNG, etc. before you open it with GIMP to edit.

---

### Post by blackened on 2010-01-19
> **jimmyUT said:**
> Did not work.  It made the whole picture gray for some reason.

Do I need to save the file in a specific format first?

You need to make sure you scan it as RGB and not grayscale. Well, you don't HAVE to, you can always convert it to RGB in GIMP after scanning by right-click->Image->Mode->RGB, then Select->By Color, select the black and then bucket-fill with the red you want. Save it and voila.

---

### Post by jimmyUT on 2010-01-19
That made the whole background red, i just need the text and the graphic to be red while keeping the white BG.

Any ideas if I am doing something wrong?

---

### Post by michy99 on 2010-01-19
Go to Color->Levels. Select the red channel. Move the bottom slider all the way to the right.

---

### Post by audiomick on 2010-01-19
Hallo.
I'm not a Gimp expert, I have only fooled around a bit. The instructions you have been given sound right. You might try zooming in to make sure you are really only selecting the black. Depending on the size of your select tool an level on magnification, you might be accidently choosing the black and the white.

In any case, Gimp can definitely do what you want, and it is not that hard either.

You could try looking here:
[http://gimp-savvy.com/BOOK/index.html](http://gimp-savvy.com/BOOK/index.html)

---

### Post by mechro on 2010-01-19
[http://publicsafety.utah.gov/bci/CFinstructorseal.html](http://publicsafety.utah.gov/bci/CFinstructorseal.html)

---

### Post by mechro on 2010-01-19
Hmm... having just posted that link I get the feeling this is all a bit dodgy. :???:

---

### Post by audiomick on 2010-01-19
> **mechro said:**
> Hmm... having just posted that link I get the feeling this is all a bit dodgy. :???:

Yeah, I did wonder myself...
Edit: on the other hand, if you can just load a PDF down, it can't be too dangerous.

---

### Post by jimmyUT on 2010-01-19
The link is for the basic format of how it should look.. I have mine with all my info on it, but obviously I don't want to post that.  Not sure what you mean by Dodgy though ??loose hinge

---

### Post by jimmyUT on 2010-01-19
> **michy99 said:**
> Go to Color->Levels. Select the red channel. Move the bottom slider all the way to the right.
OK,, that worked, awesome... now can I convert that to a pdf file or not?  I know I can insert a pdf into another pdf with Adobe Pro, but not sure if I can insert the jpeg into a pdf file

---

### Post by mechro on 2010-01-19
> **jimmyUT said:**
> The link is for the basic format of how it should look.. I have mine with all my info on it, but obviously I don't want to post that.  Not sure what you mean by Dodgy though ??loose hinge

Oh... it's just the mention of firearms and the USA makes a Brit come over all parochial. ;)

---

### Post by jimmyUT on 2010-01-19
> **mechro said:**
> Oh... it's just the mention of firearms and the USA makes a Brit come over all parochial. ;)


AH!  Bummer.  I couldn't live in a country where I wasn't able to own a firearm.  Life is too uncertain.

---

### Post by mechro on 2010-01-19
> **jimmyUT said:**
> ... Life is too uncertain.

... and the odd stray bullet in the foot is bearable!


just joking. I love America. :D

---

### Post by blackened on 2010-01-19
> **jimmyUT said:**
> AH!  Bummer.  I couldn't live in a country where I wasn't able to own a firearm.  Life is too uncertain.

Because they come in so useful on a day to day basis. Last I checked we have these awesome things called grocery stores. You should check em out. :)

---

### Post by jimmyUT on 2010-01-20
Well, I might not use mine on a day to day basis, but when the day comes that you  NEED to use one and don't have one, I bet you will have a different attitude.

And what does a grocery store have to do with anything??... I am not sure I get your Oklahoma sense of humor.

---

### Post by audiomick on 2010-01-20
> **jimmyUT said:**
>  that you  NEED to use one and don't have one, I bet you will have a different attitude.

If no-one had one, no one would need one, but let's not get into that.

Did you get your thing saved as a PDF?

From Gimp, print and tell it to print to data as a PDF

or

Open the Jpeg with the open office drawing module and export as PDF.

---

### Post by jimmyUT on 2010-01-20
I did get it done, thanks for all the help.

But your logic is completely flawed, sorry.  Criminals use other forms of weapons: knives, baseball bats, chains,  etc...even the human hand can be a weapon.

---

