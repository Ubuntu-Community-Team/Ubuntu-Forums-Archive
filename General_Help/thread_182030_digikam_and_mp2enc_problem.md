---
title: "digikam and mp2enc problem"
date: 2006-05-25
forum: General Help
---

### Post by 4ebees on 2006-05-25
Hi all,

I have 5.10 installed. I've installed mjpgtools and have located the mp2enc file (in /usr/bin/); however when I attempt to make an mpeg file with digikam it gives an error:

**********************
THE COMMAND LINE IS :

images2mpg --with-gui  -f SVCD -n PAL -d 10 -t 5 -c 000 -T /tmp/kde-patrick/kipi-mpegencoderplugin-31900/ -M /usr/include/mjpegtools -I /usr/bin -o /home/patrick/output.mpg -i  /home/patrick/Pictures/trial/DSC04576.JPG  /home/patrick/Pictures/trial/DSC04577.JPG  /home/patrick/Pictures/trial/DSC04578.JPG  /home/patrick/Pictures/trial/DSC04579.JPG  /home/patrick/Pictures/trial/DSC04580.JPG  /home/patrick/Pictures/trial/DSC04581.JPG  /home/patrick/Pictures/trial/DSC04582.JPG  /home/patrick/Pictures/trial/DSC04583.JPG 
-----------------------------------------------
Initialising...

Encoding image files...

/usr/bin/images2mpg: line 818: /usr/include/mjpegtools/ppmtoy4m: No such file or directory
-----------------------------------------------

EXIT STATUS : error during encoding process.


***********************

also attached is a screen shot of the other error I get.

Any assistance would be most appreciated.

---

### Post by coolclassic on 2006-05-25
Does the file its looking for exist? 
/usr/include/mjpegtools/ppmtoy4m

---

### Post by 4ebees on 2006-05-25
[QUOTE=coolclassic]Does the file its looking for exist? 
/usr/include/mjpegtools/ppmtoy4m[/QUOTE]

Hi coolclassic,

In Digikam I am using VCD and PAL options. 

If I run: 

whereis ppmtoy4m

I get:

/usr/bin/ppmtoy4m /usr/bin/X11/ppmtoy4m /usr/share/man/man1/ppmtoy4m.1.gz


If I change the settings in Digikam to /usr/bin/ 

I get the error message shown in the attachment.

This leads me to:

*******************
THE COMMAND LINE IS :

images2mpg --with-gui  -f VCD -n PAL -d 10 -t 5 -c 000 -T /tmp/kde-patrick/kipi-mpegencoderplugin-23963/ -M /usr/bin -I /usr/bin -o /home/patrick/output.mpg -i  /home/patrick/Pictures/trial/DSC04576.JPG  /home/patrick/Pictures/trial/DSC04577.JPG  /home/patrick/Pictures/trial/DSC04578.JPG  /home/patrick/Pictures/trial/DSC04579.JPG  /home/patrick/Pictures/trial/DSC04580.JPG  /home/patrick/Pictures/trial/DSC04581.JPG  /home/patrick/Pictures/trial/DSC04582.JPG  /home/patrick/Pictures/trial/DSC04583.JPG 
-----------------------------------------------
Initialising...

Encoding image files...

Images encoding (%) : 0      [0      
   INFO: [yuvscaler] yuvscaler 1.6.3-rc2 (15-02-2004) is a general scaling utility for yuv frames
   INFO: [yuvscaler] (C) 2001-2004 Xavier Biquard <xbiquard@free.fr>, yuvscaler -h for help, or man yuvscaler
**ERROR: [ppmtoy4m] Expecting maxval == 255, not 65535!
-----------------------------------------------

EXIT STATUS : error during encoding process.
******************

Any ideas?

Thanks for the assistance :)
Much appreciated.

---

### Post by jabeez on 2006-06-26
pretty much the same here, how friggin' frustrating. This is just one of those things in linux that drives me insane, then eventually back to winblowz if it takes long enough to figure out. What get me is, with Debian isn't the whole dependency thing meant for crap like this? I mean, if I apt-get or whatever the digikam package, shouldn't whatever packages that are needed for the program to work proplerly be downloaded? Nope, with linux it's a crapshoot. Download the program, eventually find stuff that don't work and then go searching thru forums and try your luck. Aaaaaargh, sometimes $150 for winblows seems like a helluva deal if you value your time.

---

### Post by coolclassic on 2006-06-26
install imagemagick and see how you get on.

---

### Post by 4ebees on 2006-06-28
Hi Coolclassic,
I already have imagemagick installed :(

---

### Post by jabeez on 2006-06-29
me too....

---

