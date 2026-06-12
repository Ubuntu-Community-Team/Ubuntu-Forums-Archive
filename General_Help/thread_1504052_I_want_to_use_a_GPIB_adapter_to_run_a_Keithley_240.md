---
title: "I want to use a GPIB adapter to run a Keithley 2400 SMU, and use run Lab Tracer II"
date: 2010-06-07
forum: General Help
---

### Post by logos2501 on 2010-06-07
**I want to use a GPIB adapter to run a Keithley 2400 SMU, and use run Lab  Tracer II** 			
 			 			 		   		 		 		My back story is: I've used Windows my entire life and have very limited experience with Linux and programming (a little bit of C and C++).

My current story is: I have a Dell laptop running Ubuntu Linux 9.04. Soon I will be using a Keithley 2400 SMU (Source Measure Unit) to do some characterization (current-voltage stuff). To use it I will be using the Keithley KUSB-488A GPIB adapter, which I have found linux drivers for. To run the SMU I want to use a program called Lab Tracer II (available for free on the Keithley site) which is for Windows only. 

My big question is: is it possible to make this setup work if I use Wine or Qemu to simulate Windows so that I can run Lab Tracer? Will Lab Tracer be able to "talk" to the adapter and the SMU if it's in a Windows simulation? If not, is there a Linux equivilant of Lab Tracer II? If not, what would I need to know to write such a program?

Thanks in advance for your help.

---

### Post by tgalati4 on 2010-06-07
Do you need just data logging or more complicated test-control automation?

I've seen a linux port of an older version of NI's labview.  Do you have detailed specs on the Keithley 2400 card?  If so, and if you only need data logging, then you could write a script to capture data from the /dev/gpio device.  (The actual device label will depend on the driver that you found.)

I presume that the interface is USB from the computer to 488 serial then to GPIO to the acquisition card?

---

### Post by logos2501 on 2010-06-07
I would prefer  test-control automation, but I can live with data logging for now.  I don't have any specs, unfortunately.  What would I use to write scripts? Python?  Yes, the 488 adapter is a USB device.   Also, know of any good resourcses for learning C?

Thanks.

---

### Post by tgalati4 on 2010-06-07
Python would be good for simple front-ends for data collection.

With a lot of effort, you could install a WindowsXP virtual machine to run labview or lab tracer (which I am not familiar with).  I don't know how well the virtual USB interface will work since you are trying to collect real-time information from an asyncronous port (USB) using a syncronous protocol (GPIO) through a virtual machine.  I just sense some issues with this setup.

I know that National Instruments had extensive C libraries for their acq cards and you could use that as a starting point.  Look at the Keithly 2400 card and determine what the significant acquisition chip is.  Once you have that, the rest is switching and buffering.  If you can find a linux driver for the main acq chip, then you are 1/2 way there.

For C-programming, you will have to google it.  There's a lot out there.  

If you can determine what NI card is closest to the keithley card then I can dig up what I have for C code for the NI card.  They are usually pretty close hardware and function wise.

Another issue to contend with is zero-ing out bias and self-calibration.  Normally you have proprietary Windows utilities for those functions.  Under linux, you might collect data, but without the ability to self-calibrate the card and zero-out shunt errors, then your data would be suspect.

---

### Post by logos2501 on 2010-06-08
Oh man, that sounds like a huge pain in the butt.  And if there's any reason to think the data is suspect then I think it would be better to go with a windows machine, since I'm trying to do some serious research.  

Thanks for the help!

---

### Post by tgalati4 on 2010-06-08
I have some older NI cards that I wanted to set up on a linux box, but I came to the same conclusion.  If I don't have the low-level utilities needed to recalibrate and test the cards, then collecting data from them is difficult without that pedigree.  For instance if you have a simple, 8-channel, voltage-sensing card, it has one Analog-Digital converter and an 8-way strobe switcher.  Let's say you are measuring 0 to 10 VDC and you want a linear, digital response.  You shunt all eight channels and you would expect 0.0 volts on each.  But instead you get some bias (say .1 to .2 VDC) on each.  You need a method to zero-out that bias.  The NI cards have Windows utilities that interact with the card and perform that function.  No such utilities in Linux, although you can probably write routines that perform that with enough documentation.

Now let's say it's a 16-bit card.  You have 0 to 65,536 digitization values to work with.  Most acq cards use -32K to +32K over a range of -15VDC to +15VDC.  Depending on your precision requirements, you may want to remap 0 to 10 VDC to -32K to +32K.  Again, you need the Windows utilities to perform this mapping or write your own routine to perform the transformation.  Yes, a pain in the butt.

But you only have to write the routine once.  Then you are good to go.

---

### Post by logos2501 on 2010-06-08
> But you only have to write the routine once.  Then you are good to go.

That's true.  Maybe I'll attempt it when I know more about Linux and programming.  

Thanks for your help!

---

