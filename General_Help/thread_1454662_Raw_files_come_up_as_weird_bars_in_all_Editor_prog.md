---
title: "Raw files come up as weird bars in all Editor programs"
date: 2010-04-14
forum: General Help
---

### Post by Mostly.Harmless on 2010-04-14
Hey guys,

I haven't put this in the forums for any of the separate programs, because im having the same problem in all of them, im thinking maybe its a problem elsewhere?

I recently got a Canon DSLR. It can save in Raw format, I use this function. Canons Raw format is "Whatever.CR2"

F spot viewer and all editor programs see then and 'preview' them with no problem. The images appear to have no problem until you load them into GIMP (with UFRAW) UFRAW standalone, RAWStudio etc.

They load, but only as a small vertical rectangle. Often very purple in colour. 

I thought maybe it was something wrong with just the way it looked, so I just loaded one, went save as (a jpeg) and then loaded it up, it loaded as a small picture of the same purple-haze bar.

Have I done something wrong? I googled it, downloaded UFRaw, even Ubuntu studio, same problem before and after studio installation. All these programs claim to read raw images.

Just as an example, In RawStudio:

I load up the folder of raw images. I can see all the images clearly with no problems in the preview slider up top. I can scroll through them and see them all no problem. When I click on one, it loads in the editing box as some weird bar (always vertical in orientation) often faintly resembling part of the photo but with seriously acid trip colours. Eg massive purple hazes, green everything etc.



cheers for any help

---

### Post by nixclusive on 2010-04-15
Hmm, would you upload a sample file if it isn't too large? I've never really seen a RAW image. Or perhaps you use [dcraw](http://en.wikipedia.org/wiki/Dcraw) to decode the images. :)

---

### Post by Mostly.Harmless on 2010-04-15
I would happily do anything to assist the solving of this problems. 

I dont know what too large is. Raw files on a DSLR can be big files, mine are usually 30mb per picture

Oh, If it helps anyone, I have just been informed by a photography buff friend that new model cameras often have difficult with Raw files when they first come out. Editing programs need new codecs or something to work with the files. So it may be a case of the programs are working, but I need to wait until the editing programs are updated for use with my camera.

I have a Eos 550D/KissX4/RebelT2 Which was only released in the past months..

---

### Post by akakingess on 2010-04-15
Can you not use F-Spot to save it into a different format?

---

### Post by ions on 2010-04-17
I'm having a similar problem. I changed the colour space on my 7D from sRGB to Adobe RGB. After doing so UFRaw, or any other raw editor I have installed, loads raw files like this: 

[img]http://home.cogeco.ca/~ionsvw/images/7D/UFRawproblem.jpg[/img] 

So I switched back to sRGB. The problem remains. Every raw file I have taken since changing to Adobe RGB and back to sRGB loads this way. Raw files taken before the initial change still load properly. 

To fix this I installed the icc-profile from the Ubuntu repos. Nothing changed.

I'm assuming it has to do with the colour space selection but I'm not positive.

---

### Post by ions on 2010-04-17
This is a jpeg (I shoot both raw and jpeg) of the same image straight from camera. 

[IMG]http://home.cogeco.ca/~ionsvw/images/7D/FerrisWheel1.jpg[/IMG] 

That raw image isn't a crop, that's how it opens.

---

### Post by jasonw.uk on 2010-04-19
Just a "me too" - I have a 7D, trying to see raw files on ubuntu with ufraw, I get a vertical slice of my photo with a very strong magenta cast.

Worked fine on ufraw on Windows.

---

### Post by Balian on 2010-04-19
I had similar colour problems with my Panasonic FZ35's RAW format I tried Digicam, RAWstudio, Darkroom, even GIMP with UFRAW and had no joy, that magenta was unacceptable.

I finally tried[ rawtherapee 3.0]("http://www.rawtherapee.com/?mitem=3") and had success!

---

