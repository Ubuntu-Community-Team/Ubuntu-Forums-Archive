---
title: "Help with installing.bin file for my scanner"
date: 2010-05-24
forum: General Help
---

### Post by shazzer on 2010-05-24
HI Guys

Im really stuck I have an old benq scanner 4300U and have read lots of  help about installing new firmware but as a dummy user of ubuntu from  the point of view of working in terminal, can somebody please help me.  I've saved the .bin file in a folder how to I get it working from  terminal I need a step by step guide please of exactly what to type  including whether there should be spaces or not. 

Hopefully then the system will let me use the scanner. If i use simple  scan im getting a message saying failed to use scanner but the scanner  is listed in the drop down list so guess its either a driver or firmware  issue.

Im using 10.04 lts lucid lynx.

thanks a lot for any help.

---

### Post by lisati on 2010-05-24
Moved to "General Help" from FF&H, this isn't a report of technical problems with the website here (i.e. broken features), or a question pertaining to forum features.

---

### Post by Grenage on 2010-05-24
Generally, bin files need to be made executable before running:

```
chmod +x *xxxx*.bin
./*xxxx.bin*
```

---

### Post by wojox on 2010-05-24
At first you have to open a terminal/bash and then enter, then go to the directory the .bin file is in::

```
file /path/file.bin 
```

Then:

```
chmod +x file.bin
```

And lastly :

```
./filename.bin
```

---

### Post by Sealbhach on 2010-05-24
First, right-click on the file, select Permissions and allow executing the file as a program.

Then go to Synaptic Package Manager and install nautilus-open-terminal.

Once that's installed, go to the folder where the bin is.

Right-click on an empty space and select open terminal here.

Then run this command:

```
./nameofyour.bin
```

If it complains about permissions run

```
./sudo nameofyour.bin
```

Obviously, you replace "nameofyour" with the actual name of the file.

.

---

### Post by jerome1232 on 2010-05-24
you need to set it as executable then run it.

You didn't give alot of info but since this is a driver I'm going to assume it needs root privileges... you go this driver from a reliable source right?


So let's try it with out root privileges first

Right click it, click properties, check the box next to "Allow executing file as a program", close the properties window, double click the file, click run file in terminal, it should do it's magic.


If you get some permission errors then it probably needs root privileges. Put it on your desktop. You'll need to open a terminal (Applications -> Accessories -> Terminal
```
sudo Desktop/nameofFilehere.bin
```

---

### Post by shazzer on 2010-05-24
Did what everyone advised but got a whole load of ? in bubbles an wierd script and something saying no such file or directory then the file name, line 8 syntax error near unexpected token...

have absolutely no idea what happened.

Am i supposed to be replacing an old bin file with a new one and if so, how do i identify the bin file that the scanner was using originally.

When I ask in terminal sane to sane-find-scanner it tells me found USB scanner (vendor=0x04a5) colour.. product then Flatbedscanner 22 at libsub:003:002

Any other help  would be appreciated, I know Im being thick but as i said I'm not experienced with this at all.

Just need to know how to get the scanner working. It says that its supported in Ubuntu but don't know how to get it to work. 

Anyone who can give me step by step tips and any text to copy paste would be very very grateful, otherwise its a case of buying a new scanner to complete work I need to do which seems pointless!

Thanks again for everybody's contribution

Also did something suggested in terminal which was  scanimage -L and i got this reply

snapscan@libsub:003:002 is a Acer FlatbedScanner22 flatbed scanner

It's obviously finding the scanner but just wont let me use it!! SOOO frutstrating

---

### Post by shazzer on 2010-05-24
How about installing or  getting the driver file that is for windows and doing it through wine. this seems to be recommended for some problems like this. 

Any instructions about this option would also help as I've downloaded the driver for windows xp and saved it in case I can extract a file from here that is needed but just need to know how to go about it. some people say this corrects scanner problems if the driver is installed using wine?

Just a thought :)

---

### Post by 3rdalbum on 2010-05-24
> **shazzer said:**
> How about installing or  getting the driver file that is for windows and doing it through wine. this seems to be recommended for some problems like this.

Wine only does programs.

I know of some easy generic instructions for installing .bin files. If you get any error messages, please copy and paste them into this thread so we can discern.

Also, it sounds like your scanner might not be working properly (i.e. not a driver issue) but we'll see.

The instructions are here: [http://www.chrislees.info/ubuntu/easy-run-files.shtml](http://www.chrislees.info/ubuntu/easy-run-files.shtml)

Note that you'll want to run this file as root, so follow the directions provided for this.

---

