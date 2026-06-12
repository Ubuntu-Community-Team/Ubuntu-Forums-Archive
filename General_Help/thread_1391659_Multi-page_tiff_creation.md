---
title: "Multi-page tiff creation"
date: 2010-01-27
forum: General Help
---

### Post by Prium on 2010-01-27
Hi,

I have 4500 tiff images, each <400 kb in size, that I need to merge into one multi-page tiff file. 

So I came across ImageJ. Looked promising at first but ended up producing an error message: 

```
java.lang.OutOfMemoryError: Java heap space
	at ij.io.ImageReader.read8bitImage(ImageReader.java:43)
	at ij.io.ImageReader.readPixels(ImageReader.java:647)
	at ij.io.FileOpener.readPixels(FileOpener.java:494)
	at ij.io.FileOpener.open(FileOpener.java:68)
	at ij.io.Opener.openTiff2(Opener.java:705)
	at ij.io.Opener.openTiff(Opener.java:616)
	at ij.io.Opener.openImage(Opener.java:205)
	at ij.io.Opener.openImage(Opener.java:268)
	at ij.io.Opener.open(Opener.java:124)
	at ij.IJ.open(IJ.java:1238)
	at ij.macro.Functions.open(Functions.java:2095)
	at ij.macro.Functions.doFunction(Functions.java:134)
	at ij.macro.Interpreter.doStatement(Interpreter.java:200)
	at ij.macro.Interpreter.doBlock(Interpreter.java:511)
	at ij.macro.Interpreter.doStatement(Interpreter.java:236)
	at ij.macro.Interpreter.doFor(Interpreter.java:457)
	at ij.macro.Interpreter.doStatement(Interpreter.java:218)
	at ij.macro.Interpreter.doBlock(Interpreter.java:511)
	at ij.macro.Interpreter.runUserFunction(Interpreter.java:274)
	at ij.macro.Interpreter.doStatement(Interpreter.java:203)
	at ij.macro.Interpreter.doBlock(Interpreter.java:511)
	at ij.macro.Interpreter.runMacro(Interpreter.java:127)
	at ij.macro.MacroRunner.run(MacroRunner.java:126)
	at java.lang.Thread.run(Thread.java:619)

``` 

Seems it reached some kind of memory limit? 

Any way to increase the memory limit for java? Or perhaps there is another application that might be better for this purpose?

Cheers

---

### Post by rnerwein on 2010-01-27
hi
the first thing i'll will ask you - how much ram and swap do you have ( use: free in a command line)
next - what does: ulimit -a tell you.
you can setup the values (e.g. stack size) in /etc/security/limits.conf ).
if you do that you have to logout that the values are recognized by the system.
may be this help you.
ciao

---

### Post by Lars Noodén on 2010-01-27
Is that your own program or [imagemagick](http://www.imagemagick.org/script/) or GIMP's [script-fu](http://docs.gimp.org/en/gimp-using-script-fu-tutorial.html) / [scripting](http://docs.gimp.org/en/gimp-scripting.html) ?

---

### Post by Prium on 2010-01-27
Here's the output from 'free':

```
             total       used       free     shared    buffers     cached
Mem:       4009736    3311692     698044          0         64    1777384
-/+ buffers/cache:    1534244    2475492
Swap:      4883720       9816    4873904
```


And 'ulimit -a':

```
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) 16382
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

It's not my macro - I obtained it from the [university of minnesota's biomedical image processing lab]("http://bipl.umn.edu/node/40") and installed it in [ImageJ]("http://rsbweb.nih.gov/ij/")

---

### Post by rnerwein on 2010-01-27
hi
the output of the free and ulimit looks good for me ( but i never seen a 4gb system swaping before - caching yes). i just guess your system is running out of memory. have a look at /var/log/messages and /var/log/syslog. also try: dmesg | tail -30.
sorry i don't know a lot about java i prefere pur C.
can't help any more
ciao

---

### Post by rCXer on 2010-01-27
You can set imagej's memory from the command line.  For example...
```
imagej -x 2000
```
...will run imagej with 2000MB of memory.

---

### Post by kaibob on 2010-01-27
The graphicsmagick command-line utilities seem to do a good job of  handling a large number of files and will easily create a multi-page TIF. If the individual files are in one directory, the following command is all that is needed:

```
gm convert *.tif combined.tif
```

Graphicsmagick is in the repo's and on my computer took up about 8 MB of disk space. For more information see:

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

---

### Post by Prium on 2010-02-21
Thanks for the replies.

I used ImageMagick in the end. Worked perfectly, even when the system had used up 100% physical memory and was forced to page out. 

From the terminal: 

convert *.TIF -adjoin new.TIFF

Cheers

---

### Post by russki_drewski on 2010-07-01
Hi, I need to do a similar task, but I have a multipage tiff than I need split into individual tiffs. I have an ocr program that won't deal with multi page tiffs.

Any suggestions/help?

---

### Post by rCXer on 2010-07-01
ImageJ can do this (although it can be buggy at times).  Install it using
```

sudo apt-get install imagej

```

* Applications->Graphics->ImageJ
* File->Import->Tiff Virtual Stack...
* Browse to the multiframe tiff.
* File->Save As->Image Sequence->Ok 
* Browse to the directory where you want individual frames
* Save

---

### Post by russki_drewski on 2010-07-01
Problem ... imagej says that it can't open tiffs with the compression that my file uses. :(

---

### Post by rCXer on 2010-07-02
hmm... It seems that you may need an extra plugin to read compressed tiffs.

1. Download [ij-ImageIO_bin_1.2.4.zip]("http://sourceforge.net/projects/ij-plugins/files/ij-imageio/v.1.2.4/ij-ImageIO_bin_1.2.4.zip/download") to your home folder.

2. Copy the plugin to your imagej plugins folder.
```

cd ~
unzip ij-ImageIO_bin_1.2.4.zip
cp ij-ImageIO_.jar ~/.imagej/plugins/

```

3. Start imagej and try opening the multiframe tiff again

---

### Post by russki_drewski on 2010-07-02
Thanks for the post! That might work but I found an easier and quicker way to do it:

tiffsplit file [prefix]


I had to install the package that included this particular utility, but it worked like a dream! Super easy, super quick.


Thanks to one and all!

---

