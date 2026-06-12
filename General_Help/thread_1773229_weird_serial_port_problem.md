---
title: "weird serial port problem"
date: 2011-06-01
forum: General Help
---

### Post by mistertransistor on 2011-06-01
Hello
I'm a relative newbie to Ubuntu, but not to NetBeans/java, which I have used on Windows XP for some time. 
   I have a number of Netbeans 7.0 java apps that read a serial port emulation of a real USB port, using the RXTX serial port library on Windows plus a specific serial-USB driver. They work well, but I have a particular data-acquisition app that I want to run 24x7 on an oldish PC. After about 3 days, XP seems to run out of some system resource and things fall over.
  So, I thought I'd switch to Linux. I built a clean Ubuntu 11.4 system and installed my app plus the RXTX library. I used usbserial to emulate a serial port for the USB device - it comes up as /dev/ttyUSB0. When I start the data acquisition, it runs for a random time between 1 and 10 minutes and then hangs, with no errors on the monitor. My GUI shows no data coming from the thread that reads the emulated port. My *identical* java code on Windows XP does not have this problem.
  Can anyone tell me how to investigate this problem? I guess that there might be errors in some system log - where is a likely place to look? (Although the random nature of the period for which it works does worry me).
  I realise that I have given very little details of the code - I don't want to get into that yet. I need some general suggestions as to how to identify the problem. I suspect that RXTX is a deep pool and I'm probably not going to dive into that.

Andrew

---

### Post by mistertransistor on 2011-06-02
well I'm now tearing my hair out. The problem only occurs when the PC is in the garage, where the data source (a seismograph) is. If I move it to the house to debug it, there is no problem.
  I only move the system unit (and mouse) - so there is a different keyboard and monitor, but I cannot see how that could affect it. I guess it may be a power problem but I have checked the voltage and it's fine. Power line noise maybe?

---

### Post by cavh on 2011-06-02
As a fix, suggest checking for memory leaks in your code and fixing any, then running again on XP and see what happens. Presuming you use jUnit as a test framework, you could use Tor's blog post at [http://blogs.oracle.com/tor/entry/leak_unit_tests]("http://blogs.oracle.com/tor/entry/leak_unit_tests") as a guide

---

