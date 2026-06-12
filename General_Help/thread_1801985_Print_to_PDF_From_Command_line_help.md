---
title: "Print to PDF From Command line help"
date: 2011-07-11
forum: General Help
---

### Post by zombo12 on 2011-07-11
Hey,

I am trying to find a way to print PDFs from the command line.  I was using "cups-pdf', but I want to be able to specify the output folder from the command line.  Is there a way to do this?

I guess what I am trying to do is the Gnome "Print to file" option in the terminal so I can easily print off a batch of file to whatever directory I wanted.

Thanks for the help

Ubuntu 10.04 Lucid Lynx

---

### Post by nmaster on 2011-07-11
this method doesn't exactly work (lpr process is background'd so it tries to move a file that isn't there), but i think you'll have to do something like this:
[http://ubuntuforums.org/showthread.php?t=1353612](http://ubuntuforums.org/showthread.php?t=1353612)

this is the thread where people helped me fix it: [http://ubuntuforums.org/showthread.php?t=1358124](http://ubuntuforums.org/showthread.php?t=1358124)

---

### Post by 1chess2u Christian on 2011-07-11
This might not work, but try this:
```
<command> --help
```
or
```
<command> -h
```

---

### Post by zombo12 on 2011-07-11
> **nmaster said:**
> this method doesn't exactly work (lpr process is  background'd so it tries to move a file that isn't there), but i think  you'll have to do something like this:
[http://ubuntuforums.org/showthread.php?t=1353612](http://ubuntuforums.org/showthread.php?t=1353612)

this is the thread where people helped me fix it: [http://ubuntuforums.org/showthread.php?t=1358124](http://ubuntuforums.org/showthread.php?t=1358124)


Thanks for the replies guys.  I did something similar to what you did  before nmaster, but I want cut out the middle man and just put it  exactly where i want it.  I feel like there has to be a way to do this,  print to a directory is so easy in gnome.

> **1chess2u Christian said:**
> This might not work, but try this:
```
<command> --help
```or
```
<command> -h
```


the command to print is "lpr". You can specify a destination printer, but it is cups-pdf which specifies the output directory in cups-pdf.conf.  So unless there is another command to print to a pdf directly, the options in lpr will not help.

---

### Post by nmaster on 2011-07-11
> **zombo12 said:**
> I want cut out the middle man and just put it   exactly where i want it.  I feel like there has to be a way to do this,   print to a directory is so easy in gnome.


i agree.  i hope you figure out a way; it would be very convenient.   i really needed it that one time, but if you think of a good solution  it will most likely be very useful for me in the future.

---

