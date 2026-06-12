---
title: "Data Acquisition"
date: 2010-03-18
forum: General Help
---

### Post by Pirindingo on 2010-03-18
I'll buy a Data Acquisition system for analogic and digital signals..
I've looking the options, but I haven't found one with linux's software.

I would like to know if somebody know something with this option, or if somebody know about a generic Data Acquisition software for linux. and, in this case, wich would be the best equipment for.

Regards and thanks!

---

### Post by bobcollard on 2010-03-18
> **Pirindingo said:**
> I'll buy a Data Acquisition system for analogic and digital signals..
I've looking the options, but I haven't found one with linux's software.

I would like to know if somebody know something with this option, or if somebody know about a generic Data Acquisition software for linux. and, in this case, wich would be the best equipment for.

Regards and thanks!
You might look into Ubuntu Studio.  Don't know about the kind of hardware you are working with, but, they have all kinds of mixers and sound boards over there.

---

### Post by tgalati4 on 2010-03-18
apt-cache search acquisition

Look into older National Instrument cards on ebay or craigslist.  Check out comedi.

---

### Post by srs5694 on 2010-03-18
I'm doing some programming for a professor at the University of Pennsylvania who uses boards from [United Electronic Industries](http://www.ueidaq.com/) for data acquisition in psychology experiments. These boards have proprietary Linux drivers and sample programs. I'm not sure if they've got any "generic" data-acquisition programs for Linux; my own task is to write highly specialized software using the UEI drivers. This does work, but the drivers are a bit flaky.

---

### Post by oldfred on 2010-03-18
I have been trying to learn python and it has lots of tools, libraries that link bits of code together. You have to do a bit of programing or modify something else you find for your exact setup.

First few hits in google looked like a start if you can do some programming. Shows sample code.
python data acquisition

[http://www.scipy.org/Cookbook/Data_Acquisition_with_NIDAQmx](http://www.scipy.org/Cookbook/Data_Acquisition_with_NIDAQmx)
These are quick examples of using [ctypes]("http://docs.python.org/lib/module-ctypes.html") and numpy to do data acquisition and playback using [National Instrument's]("http://ni.com/") [NI-DAQmx]("http://www.ni.com/dataacquisition/nidaqmx.htm") library

[http://www.scipy.org/Cookbook/Data_Acquisition_with_PyUL](http://www.scipy.org/Cookbook/Data_Acquisition_with_PyUL)
This pages illustrates the use of the inexpensive (about $150) [PMD USB-1208FS]("http://www.measurementcomputing.com/cbicatalog/cbiproduct_new.asp?dept_id=412&pf_id=1665&mscssid=G9PDTGJV5VES9P694WLRS3JWG3J615M7") data acquisition device from [Measurement Computing]("http://www.measurementcomputing.com/").

This is the html version of the file [http://pyexp.sourceforge.net/Pyexp-WorkshopESRF-nov2001.presentation.pdf](http://pyexp.sourceforge.net/Pyexp-WorkshopESRF-nov2001.presentation.pdf).
**Google** automatically generates html versions of documents as we crawl the web.

---

### Post by wkulecz on 2011-02-15
While this is an old thread, its near the top when searching "comedi" at the top of the forum, so maybe this will help someone else.

Comedi is in the 10.04 repos, unfortunately while it is reasonably actively maintained what little documentation exists is quite out of date.

Here is how I got it working on 10.04

(1) In Synaptic search comedi and mark for installation everything that turns up, except for ktimetrace which is so lame as to not be worth bothering with and works so poorly you'll get the wrong idea about comedi.

(2) Exit Synaptic and do and as your normal user:
    apt-get source comedilib

(3) cd to comedilib-0.8.1 and do:
    ./configure
    make

(4) add your user id to the iocard group created by the comedi install.

(5) shutdown, install your supported comedi card, and boot.

(6) cd comedilib-0.8.1/demo and if all is well you should be able to run and examine the demo programs to get started.  If they fail, do lsmod and dmesg to see if the kernel driver module for your card installed correctly and is running.  If not, you will have to read up on comedi_config and troubleshoot to figure out what is wrong.

I've set up two systems like this, one  using a National Instruments PCI-6071E board and the other a Computer Boards PCI DAS-1602/16.

For troubleshooting your best bet will be the Comedi mailing list, most convienently accessed through Google groups.

---

