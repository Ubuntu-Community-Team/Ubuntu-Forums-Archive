---
title: "scanimage: unrecognized option '--format=pnm'"
date: 2011-10-22
forum: General Help
---

### Post by kamaji792 on 2011-10-22
I am trying to run **scanimage** from the command line (technically on my headless server).  When I try and change the file format with **--format=tiff** I get an error message:
```
$ sudo scanimage -d 'epson2:libusb:004:002' --mode Color --format=tiff > test.tiff
scanimage: unrecognized option '--format=tiff'
```

Am I doing something wrong, missing some installation or can the Epson back-end really not change the format of the output file?

It does work if I do the following:
```
$ sudo scanimage -d 'epson2:libusb:004:002' --mode Color > test.pnm
```

Thank - k

---

### Post by plucky on 2011-10-22
From **man scanimage**```
The --format format option selects how image data is written  to  stan&#8208;
       dard  output.  format can be pnm or tiff.  If --format is not used, PNM
       is written.
```

Looks like it doesn't need the =

Good Luck

---

### Post by kamaji792 on 2011-10-22
> Looks like it doesn't need the =
Hmm...
```
$ sudo scanimage -d 'epson2:libusb:004:002' --mode Color --format tiff > test.tiff
[sudo] password for bighog: 
scanimage: unrecognized option '--format'
```

If you look at the bottom of the **scaniamge man** page:

> As  you  might  imagine,  much of the power of scanimage comes from the
       fact that it can control any SANE backend.   Thus,  the  exact  set  of
       command-line  options  depends  on  the  capabilities  of  the selected
       device.  To see the options for a device named  dev,  invoke  scanimage
       via a command-line of the form:

              scanimage --help --device-name dev

The output of

[FONT="Courier New"]scanimage --help --device-name epson2[/FONT]

does suggest that **[FONT="Courier New"]--format=tiff[/FONT]** is valid.  However:

[FONT="Courier New"]man sane-epson2[/FONT]

does not have a **[FONT="Courier New"]--format[/FONT]** option.

Ultimately not that important.  There are **ppmto<img-format>** programs for most of the formats you are likely to need.

Thanks for the reply - k

---

