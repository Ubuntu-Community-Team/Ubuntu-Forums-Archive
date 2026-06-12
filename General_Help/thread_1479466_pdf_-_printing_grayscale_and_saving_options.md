---
title: "pdf - printing grayscale and saving options"
date: 2010-05-10
forum: General Help
---

### Post by user334312 on 2010-05-10
I'm using cups-pdf for pdf printing and am on 64-bit Intrepid.

1a. Is there a way to add grayscale output as an option? Or is there another virtual printer I should be using instead? (At present, I can only manipulate page size and resolution.)

1b. (This is more appropriate for the ImageMagick board but am including it here just in case.) In the meantime, I've been using ImageMagick to manually convert pdfs via command line. For some reason, I can't get the "-colorspace Gray" option to work. Running:

convert -colorspace Gray originalfile.pdf newfile.pdf

just results in another color pdf. This isn't a huge deal (my work-around is to use -separate) but I can't figure out what I'm missing. (I can paste job logs if it's helpful.)

2. Is there any way yet to force applications to remember print options/settings or to make certain choices persist? For example, I prefer to not print headers and footers when printing from a browser and have the page scaled 90%. But every time I pull up the print dialog, it displays the default settings of printing headers/footers, ignoring scaling, etc.

Thanks in advance.

(Background: I've been using Ubuntu on my primary machine for a couple of years now and generally know my way around, but I still consider myself a newbie with the basics of Linux.)

---

### Post by user334312 on 2010-05-15
(The forums rules -- [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy) -- makes no mention of bumping, but I know it's generally discouraged, so here's my self-imposed single bump. Apologies but I've googled everywhere I can think of and found no solution that's worked yet.)

---

### Post by kaibob on 2010-05-15
I tried the convert command from your post, and it worked fine. I'm running Lucid, which contains a newer version of Imagemagick, and this is one possible explanation why the command works for me but not you. 

If you can't get Imagemagick working, you may want to try graphicsmagick.

[http://www.graphicsmagick.org/utilities.html](http://www.graphicsmagick.org/utilities.html)

Another alternative is Ghostscript. I tried the following command, and it worked fine. As often as not, Ghostscript issues warnings of one sort or another--just ignore these. 

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray -sOutputFile=output.pdf input.pdf
```

[http://handyfloss.net/2008.09/making-a-pdf-grayscale-with-ghostscript/](http://handyfloss.net/2008.09/making-a-pdf-grayscale-with-ghostscript/)

To get grayscale images with cups-pdf, you can uncomment and modify the GSCall line in the cups-pdf.conf file utilizing the grayscale settings in the above Ghostscript command. I haven't made this particular change, but I have modified the cups-pdf.conf file, and this should work fine.

As far as making grayscale an option with cups-pdf, the only method that comes to mind is to use the cups-pdf post-processing option to convert (with Imagemagick or Graphicsmagick or Ghostscript) the color PDF to grayscale. Doing this is a bit complicated and probably a more involved undertaking than you are interested in. See the following thread for some background on cups-pdf post processing scripts. 

[http://ubuntuforums.org/showthread.php?t=1382024&highlight=cups-pdf+post+processing](http://ubuntuforums.org/showthread.php?t=1382024&highlight=cups-pdf+post+processing)

The forum moderators have stated that bumping a thread is allowed once every 24 hours. 

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

---

### Post by user334312 on 2010-05-16
Thanks, kaibob. Both Graphicsmagick and Ghostscript did the job. The GM version was a slightly lower-res while GS was crisp, and both were around the same file size as the original. I'll continue playing around with options on both to see which works best for me.

I'll also give post-processing a try. I don't mind tinkering with scripts and settings at all. Anything that helps me get better acquainted with Linux is good.

And thanks for the info on bumping. I hadn't seen that. I figured better safe than sorry!

---

