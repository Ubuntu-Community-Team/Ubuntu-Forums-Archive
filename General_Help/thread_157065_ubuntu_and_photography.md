---
title: "ubuntu and photography"
date: 2006-04-08
forum: General Help
---

### Post by Shay Stephens on 2006-04-08
Now that I have been using ubuntu long enough to get my bearings, I am ready to start trying to put this to use.  I am a photographer and currently have to do all my editing in Photoshop.  My plan is to eventually do it all in ubuntu.  Here is what is currently holding me back: ](*,) 

[LIST]
[*]Can't find a way to profile my monitor.  I have a gretag macbeth eye-one.
[*]Processing RAW and editing images in 16bit.
[*]Making a DVD slideshow with "ken burns" effects ala [Memories on TV]("http://www.codejam.com/")
[*]Printing on DVD's with a Primera Signature Z thermal printer.
[/LIST]

I was happily using Memories on TV until recent updates broke my functionality.  So my last mental impediment to switching to 100% ubuntu is now gone.  The equipment listed is what I have, but I am not opposed to buying new equipment.  I really need something that will work if this is going to fly.

I have recently discovered Bibble Pro will work in Linux and that should let me process RAW in 16 bits.  And I have read about CinePaint which should let me edit images in 16bit as well.  I will be trying those out soon.

So that really leaves the monitor profiling, slideshow, and printing.  Does anyone have suggestions?  What are you using?  Has this been brought up before?  If so, anyone have some links?  Any help would be appreciated :D .  I will be updating this post as I make discoveries.

---

### Post by mips on 2006-04-08
Wait about 2 weeks for Cinepaint Glasgow, [www.cinepaint.org](www.cinepaint.org)

[http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/](http://www.etg.e-technik.uni-erlangen.de/web/doe/xcalib/)  allows you to tranfer profiles from one os to another.
There must be a way to do hardware calibration as lots of movie studios use linux and I cannot see them not doing calibration.
[http://applications.linux.com/article.pl?sid=05/02/07/2244242](http://applications.linux.com/article.pl?sid=05/02/07/2244242)
[http://www.linuxmovies.org/software.html](http://www.linuxmovies.org/software.html)


[www.caldera.fr](www.caldera.fr)

[http://www.linuxjournal.com/article/6635](http://www.linuxjournal.com/article/6635)

[http://dvd-slideshow.sourceforge.net/](http://dvd-slideshow.sourceforge.net/)  is a possible slideshow application. Theres probably more out there. K3b is a good cd/dvd authoring tool.

[http://www.linuxprinting.org/](http://www.linuxprinting.org/)
[http://www.faqs.org/docs/Linux-HOWTO/Printing-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Printing-HOWTO.html)
[http://www.fogman.de/?GnomePhotoPrinter](http://www.fogman.de/?GnomePhotoPrinter)
[http://xwtools.automatix.de/](http://xwtools.automatix.de/)
Should be many more.

```
Printing on DVD's with a Primera Signature Z thermal printer.
```
I doubt you are goint to get it to work but hopefully I'm wrong.

Can also do a search in the PC Tools section of DPreview for "linux"

---

### Post by Shay Stephens on 2006-04-08
Thank you mips, this looks like pure gold!  I am excited to see what the glasgow version is going to do.  I will start exploring those links you have posted.

Thanks again!  =D> \\:D/

---

### Post by mips on 2006-04-10
Pleasure, let us know how it goes.

---

### Post by Totzo on 2006-04-19
have you tried [lightzone]("http://sonic.net.nyud.net:8080/~rat/lightcrafts/")? It costs a fortune for windows and mac but it's free for linux users! One of the developers is a linux fan apparently.

I use a D100 and the colour seems a bit washed out using it but you may have a  diferent experience,

T

---

### Post by graigsmith on 2006-04-19
> # Processing RAW and editing images in 16bit.

Search synaptic for ufraw, it's in the universe repositories.  It allows you to edit what your image looks like before you import it to gimp.  You can edit contrast, exposure, white balance, and blackpoint.  All that is 16 bit editing, it converts to 8 bit when you import it to gimp, which is ok. Because you should have most of the problems out of your image after ufraw.  heres a ufraw screenshot.

[IMG]http://webpages.charter.net/graigsmith/rawfiles.png[/IMG]

Why this doesn't come installed by default is beyond me.

---

### Post by jasplund on 2006-04-20
[QUOTE=graigsmith]Search synaptic for ufraw, it's in the universe repositories.  It allows you to edit what your image looks like before you import it to gimp.  You can edit contrast, exposure, white balance, and blackpoint.  All that is 16 bit editing, it converts to 8 bit when you import it to gimp, which is ok. Because you should have most of the problems out of your image after ufraw.  heres a ufraw screenshot.

[IMG]http://webpages.charter.net/graigsmith/rawfiles.png[/IMG]

Why this doesn't come installed by default is beyond me.[/QUOTE]

What version of ufraw is that? It doesn't look like the one I've got from universe.

---

### Post by graigsmith on 2006-04-20
it is the exact same one from universe. hmm. i wonder if different functions are enabled or disabled for certain raw formats?  cause thats what i can edit on my pentax * ist d raw files.  what kind of camera do you have?

here are the supported cameras
[http://ufraw.sourceforge.net/Cameras.html](http://ufraw.sourceforge.net/Cameras.html)

---

### Post by jasplund on 2006-04-20
[QUOTE=graigsmith]it is the exact same one from universe. hmm. i wonder if different functions are enabled or disabled for certain raw formats?  cause thats what i can edit on my pentax * ist d raw files.  what kind of camera do you have?

here are the supported cameras
[http://ufraw.sourceforge.net/Cameras.html](http://ufraw.sourceforge.net/Cameras.html)[/QUOTE]

I'm using a Konica-Minolta Dynax 7D

I don't have that curve correction thing

---

### Post by graigsmith on 2006-04-20
hmm, mabey its just shrank? as you can see from the screenshot, theres a color management, and white balannce that i have shrunk.  if you click them they expand.  mabey yours is like that.  if not, i have no idea why it wouldn't display it.

---

### Post by jasplund on 2006-04-21
Well that's not it. Mine looks likte the attachment

---

### Post by graigsmith on 2006-04-22
whats that corrections tab right next to base?

---

### Post by jasplund on 2006-04-23
[QUOTE=graigsmith]whats that corrections tab right next to base?[/QUOTE]

this is the corrections tab

---

### Post by graigsmith on 2006-04-24
you should be able to use the exposure slider and then be able to adjust the curves. and that should give you anything you want out of it.

in fact since you have a curves dialog there, it should actually give you more control that what i have been using.

hmmm, are you using dapper? or breezy?
im using breezy.

---

### Post by jasplund on 2006-04-24
yeah I kow I'm just surprised that it's different

---

### Post by Shay Stephens on 2006-04-24
I have been able to get photoshop 7 to load via wine.  CS and CS2 won't work yet.  But PS7 is a good start.  At least it lets me easily create and use actions for batching photos.

On the slideshow front, I was able to get Memories on TV to load and run via wine also.  So problem solved there too.

I am still waiting on cinepaint glasgow to launch.  I would like to test it's abilities.

I have also used the demo for bibble.  It can load and process 16bit raw files.  The work flow is pretty different from what I am used to in PS-CS2, but it has noise reduction built in and does most of what I need.  I would still like to see vignette control addes however.

A combo of cinepaint and bibble might be just right in the future.

Things still needing to get done.  Being able to profile a monitor (LCD) and printing to my DVD thermal printer.

I am assembling the bits together.  Thank you all for your suggestions to date, and I do hope for more input as the weeks pass.  I can't load dapper yet, but I am hoping that will help out things here.  As soon as I have some stable results and I have done some real work with it and not just feasability tests :D .

[QUOTE=Shay Stephens]

[LIST]
[*]Can't find a way to profile my monitor.  I have a gretag macbeth eye-one.
[*]Processing RAW and editing images in 16bit.
[*]Making a DVD slideshow with "ken burns" effects ala [Memories on TV]("http://www.codejam.com/")
[*]Printing on DVD's with a Primera Signature Z thermal printer.
[/LIST]

[/QUOTE]

---

### Post by cypresstwist on 2006-04-27
I have a Phillips camera that makes only .RAW images. To convert them to something readable I use dcraw and a small script that goes like this:

#!/bin/sh
for i in *.RAW; do dcraw -c "$i" | cjpeg > "`basename "$i" .RAW`.JPG"; done

I run it in a directory where I put my .RAW files. You can also add a line to the script that will delete the .RAW images after they're processed. 
Hope this helps someone :)

---

### Post by PereUbu on 2006-07-29
Hi Graigsmith!

How did you get the previews of your rawfiles in nautilus?
I have a Pentax istDS but my previews are blank, so i have to use Picasa to browse my photos :-( 

Best regards 
PereUbu

---

### Post by Jado on 2006-08-23
Hey, guys.

I installed uFRaw, except I don't know see it on any of the pulldown menus (Applications, Places, System). I basically have no idea how to fire it up and view my RAW files with it. Or I meant to use it while in Gimp... though my understanding is that there's a GIMP plugin and a standalone. I'm looking for where the standalone went to.

---

