---
title: "What the hell is wrong with printing photos in Linux????"
date: 2011-04-24
forum: General Help
---

### Post by quickk on 2011-04-24
Hi everyone, 

   I have spent the last 5 hours trying to simply print a 4x6 photo, and a passport sized 2x2.75 inch photo.   I have tried with the Gimp, Digikam, Gwenview, etc.   What happens is that I set everything up, and then the photo that comes out is purely random in size.  

For example, using the Gimp:

-I got to image->print size and specify that I want a 4 by 6 image.
-This does not actually do anything.  When I select print, these specifications are ignored.

-I try again.  This time, in the print dialogue, I go to image settings are select width of 4 inches, height 6 inches.   I press print, and the image is 50% smaller than expected.  I notice after the fact that somewhere else the page setup set the scale factor to 50%.

-I try again.   This time I make sure that the scale is 100%, I select the right image size in the image settings, I have double checked the paper size, turned off the "reduce/enlarge" in the advanced dialogue (even though I don't know what these options do... I can't find any documentation for the print options).   I try printing again and now the image is about 10 % too big, and half an inch is missing all the way around.   Apart from that the photo is bordless, just too big.

I now give up and try digikam:

- I select my image, go to print images and click the option button on the bottom.   I click the image settings tab, select "scale to" 4x6 inches.   I print, and the image is 50% too small.   #@%&$%&!   
- I try five more times, and can't figure out why this happens.   
- I try the print wizard, which is completely useless.

I could go on and on.   Why is this so damn difficult?  What am I missing?

---

### Post by earthpigg on 2011-04-24
My brain just leaped to two things:

"open with firefox, and print there!" (note, this may have leaped to mind because im in firefox right now...)

and

"put it in an openoffice document, print from there!"

and

"put it in openoffice presentation, print from there!"


though, honestly, i've never tried printing a picture to specific custom sizes so cannot tell you if either approach is sound. maybe it was just the fresh perspective you needed :)

---

### Post by bouncingwilf on 2011-04-24
Er... I use photoprint    Applications -> Graphics. If it's not installed, it's in the repos. I find it quite easy to size with this using borders etc. 


Bouncingwilf

---

### Post by decrepit on 2011-04-24
It may be a resolution problem.
If I'm using gimp, I "scale" the image to the exact size I want at the resolution I want, (say 300dpi).
If the printer is then set to 300dpi, you should get the size of image you've set.

---

### Post by quickk on 2011-04-24
Thanks for the advice everyone.    I was getting quite frustrated yesterday.  

I will give the openoffice options a try, but I am still bewildered as to why I can't print properly from my photo software.   

decrepit:  I've tried "scaling" the image to the wanted size in Gimp, but this does not seem to have any effect.   Also, the dpi resolution of the printer is not related to the ppi resolution in the Gimp.

---

### Post by earthpigg on 2011-04-25
> **quickk said:**
> 
I will give the openoffice options a try, but I am still bewildered as to why I can't print properly from my photo software.   


such software falls into either the 'casual social networker' category, or into the 'professional photo manipulation' category.

former, printing is not a development priority.

latter, these guys hand it off to printer people (ie: the folks putting the image into the magazine advertisement, etc) to print.

:P

---

### Post by quickk on 2011-04-25
> such software falls into either the 'casual social networker' category, or into the 'professional photo manipulation' category.

former, printing is not a development priority.

latter, these guys hand it off to printer people (ie: the folks putting the image into the magazine advertisement, etc) to print.

Makes sense, however in my opinion this is one of the reasons why Ubuntu, and Linux as a whole is not more widely adopted.   Start by the basics!   If a computer user cannot easily perform basic tasks like printing, then there is no hope to get the operating system widely adopted.  All it takes is one bad experience and then the person experimenting with Linux won't give it another shot.  

I can't stand Windows and OS X, and have been using Ubuntu since 6.10, however I can't get my wife to even consider using Linux.   The other day she was in a bind and tried to use my desktop to print a passport photo and was not able to.   She also tried loading some music onto her iphone and failed again (a newer version of libimobiledevice was needed).  I know the iphone problems are not Canonical's fault, however I swear that iron-clad iphone/ipod support (even though I hate the devices) would bring much more users to Ubuntu than completely revamping the GUI.   

I would much rather have iron-clad support for the basics than adding new bells and whistles.   Anyway... looks like this post turned into a rant so I'll stop now!

---

### Post by decrepit on 2011-04-26
> **quickk said:**
> >>>>>>>  

decrepit: >>>>   Also, the dpi resolution of the printer is not related to the ppi resolution in the Gimp.

It's not automatically related, that's the problem, you have to set both the same. If the printer's dpi is higher than you've set in the gimp, the photo may come out smaller. If the printers dpi is lower than that set in the gimp the picture may be bigger.
If they're the same, and there's no other scaling set, the size should be right.

---

### Post by Mark Phelps on 2011-04-26
It's been a while, but when I was printing photos in Gimp, I found Gutenprint to be a valuable addition.  It allowed for lots of customization of the printing features.

---

### Post by Ubuntu Warrior on 2011-04-27
Cannot agree more with this post. I have struggled a lot with printing in Ubuntu Linux (and other flavours for that matter) and cannot for the life of me understand why!!! If I boot into Windows 7, open a pic and print it out to a 4x6 photo on an HP Photosmart printer it works pretty well without playing around with settings for hours. I hate to point out cases where MS has the advantage over Linux as I am a dedicated Linux supporter but this type of issue does explain why most people steer clear of anything but Windows. Missing an opportunity???

---

### Post by quickk on 2011-04-30
> I found Gutenprint to be a valuable addition

Where do you get Gutenprint?   I couldn't find it in the repositories, and it really isn't clear to me what this is.

---

### Post by JKyleOKC on 2011-04-30
> **quickk said:**
> Also, the dpi resolution of the printer is not related to the ppi resolution in the Gimp.Not really an accurate statement. The ppi you set for the Gimp determines the number of pixels in the generated image; if you set it to 300 ppi and the size to 4x6 inches, the image will consist of 1200 lines with 1800 pixels per line. The dpi resolution of the printer determines the size that it will give each pixel. If it's at 150 dpi, your 1800 pixels per line will give a printed line that's 12 inches long, and if the printer is set for 600 dpi, the line will be only 3 inches long.

The only way to get what you want is to make sure that both the printer and the Gimp are set for the same number of dpi/ppi, and also make sure that scaling is turned off both places.

FWIW, my printers seem to default to 1200 dpi settings but can be changed on the fly...

---

### Post by quickk on 2011-05-06
Ok, I am now going to loose my mind.   I need to print a pdf document.   It is in color and has one photo in it.   The document is letter sized.   It opens up in Okular, I select print, change every possible option (at least three in two different places) so that it prints on letter paper (8.5 by 11 inches), press print and then lo and behold a 4x6 print come out of the printer.   WHAT THE HELL!!????!!!   I tried again, perhaps I missed something.   Same result.   Why is the simple act of printing so damn impossible?  You shouldn't have a physics PhD to figure out how to print a simple letter sized document in Linux.   Oh wait.  I actually do have a physics PhD, and I still can't get the stupid thing to work.

---

