---
title: "cannot print in Lubuntu"
date: 2011-12-28
forum: General Help
---

### Post by rng on 2011-12-28
I am using Lubuntu 11.10 and my printer (HP laserjet 1020) is being recognized but on printing documents, the job is stopped and in attributes there is message that: '/usr/lib/cups/filter/foomatic-rip failed'

How do I solve this? Thanks for your help.

---

### Post by 2F4U on 2011-12-28
There should be log files in the directory /var/log/cups, which may give more detailed information about the error.

---

### Post by rng on 2011-12-29
It is a large file with same error message: '/usr/lib/cups/filter/foomatic-rip failed'

---

### Post by JC Cheloven on 2011-12-29
Hi rng, I came here from [this]("http://ubuntuforums.org/showthread.php?t=1900486&page=2").

I don't have a 1020, but a 1010 (which despite the name is pretty different regarding linux, I think). But I see that the package "foo2zjs" is (at least at some time was) needed for that printer. From the info provided in synaptic:
> foo2zjs is an open source printer driver for printers that use the
Zenographics ZjStream wire protocol for their print data, such as the
Minolta magicolor 2200/2300/2430 DL, Minolta Color PageWorks/Pro L and
HP LaserJet 1000/1005/1018/1020/1022. These printers are often
erroneously referred to as "winprinters" or "GDI printers".

This package provides the following drivers: foo2hiperc, foo2hp,
foo2lava, foo2oak, foo2qpdl, foo2slx, foo2xqx, foo2zjs.

The foomatic-db-engine package is recommended to simplify configuring
this printer driver.  The psutils package is needed to enable n-up
printing support.
Also I found this related page, that you should evaluate on your own (I'm not endorsing it, simply I found it) [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

If it worked in previous versions of ubuntu, perhaps this is a regresion... don't know really, but hope to have given a hint.

---

### Post by rng on 2011-12-29
@JC Cheloven: Thanks for your help. I installed hplip and hplip-gui from apt-get and ran the command 'hpsetup -i'  and also tried to adjust settings from [http://localhost:631](http://localhost:631) and from the printing option in system tools. Now the printer has started working, though I am not sure what has been the main correction. I can now see the "hp" icon on panel so I guess hplip installation has done the trick. Your info and links point to exactly what I wanted and I will use it if I have any problems again. 

Best wishes,
rng.

---

### Post by amjjawad on 2011-12-30
I'm glad that JC has a printer as I don't :)

---

### Post by JC Cheloven on 2012-01-02
> **amjjawad said:**
> I'm glad that JC has a printer as I don't :)
A collection for a printer is in order. Amjjawad deserves it :D

---

### Post by dvdcnl on 2012-01-09
I'm having the same problem with a hp cp1215.  Printer works in windows.   Log says 'stopped' right after I press the print button.  I'm a newby so I would appreciate a step by step 'how to".   Using Lubuntu 11.10

Thanks,  David

UPDATE:   prints in b&w...no color.   Still working on it.

---

### Post by amjjawad on 2012-01-12
> **JC Cheloven said:**
> A collection for a printer is in order. Amjjawad deserves it :D

Hey, thanks :D

@OP
Kindly mark your thread as SOLVED if you don't have any other Q regarding the same subject :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by amjjawad on 2012-01-12
> **dvdcnl said:**
> I'm having the same problem with a hp cp1215.  Printer works in windows.   Log says 'stopped' right after I press the print button.  I'm a newby so I would appreciate a step by step 'how to".   Using Lubuntu 11.10

Thanks,  David

UPDATE:   prints in b&w...no color.   Still working on it.

Hello and Welcome to Ubuntu Forum :)
Also, thanks for choosing and using Lubuntu!

Lubuntu One Stop Thread (my signature) will help you for general information about Lubuntu. As for your specific issue, have you checked JC's post?

---

