---
title: "Ubuntu automatically shutting down"
date: 2010-10-18
forum: General Help
---

### Post by shaquille on 2010-10-18
I am using Ubuntu 10.04. It is installed in windows xp. Recently I am facing a problem. After starting the computer and boot into Ubuntu, it works fine but after sometime, at about after an hour it just automatically shut down. I don't know why. My xp is doing fine but the problem in only Ubuntu.

Any suggestion for me?

---

### Post by aboud on 2010-10-20
it looks like hardware problem.

---

### Post by matsuzine on 2010-10-20
Are you receiving any messages before shutdown?

"It is installed in windows xp" --> do you mean that you are running it using virtualization or installed with wubi, or something else?

Thanks

---

### Post by TBABill on 2010-10-20
Is it heat related? Does the machine feel hot or is this a desktop where you may not be able to tell?
 
If you think it could be heat related you can do an easy install of lm-sensors and use a terminal to check temps. If you don't like the terminal there are applets for various temperature monitors. 
```
sudo apt-get install lm-sensors
```
That's LM-SENSORS in lower case, not an I or a 1. Once installed all you have to do is type the word sensors in a terminal for output of temps. Many systems approach critical between 90-110 degrees celcius. My systems are 99C or 100C where they automatically shut off. 
 
If the problem is heat related there are steps you can take to help lower the heat. What are you doing when the system shuts down? Web surfing, watching videos, etc?

---

### Post by shaquille on 2010-10-25
> **TBABill said:**
> Is it heat related? Does the machine feel hot or is this a desktop where you may not be able to tell?
 
If you think it could be heat related you can do an easy install of lm-sensors and use a terminal to check temps. If you don't like the terminal there are applets for various temperature monitors. 
```
sudo apt-get install lm-sensors
```
That's LM-SENSORS in lower case, not an I or a 1. Once installed all you have to do is type the word sensors in a terminal for output of temps. Many systems approach critical between 90-110 degrees celcius. My systems are 99C or 100C where they automatically shut off. 
 
If the problem is heat related there are steps you can take to help lower the heat. What are you doing when the system shuts down? Web surfing, watching videos, etc?

Yeap I think the problem is heat related.

---

### Post by Dans564 on 2010-10-25
my suggestion would be to scrap wubi.  wubi has all sorts of problems and executing a real dual boot is super easy with the new installer for 10.10.  As easy if not easier then wubi.

---

### Post by endotherm on 2010-10-25
just to clarify, does it shutdown gracefully as it should, or does it just die with a black screen, and straight to bios load?

---

### Post by endotherm on 2010-10-25
> **TBABill said:**
> Is it heat related? Does the machine feel hot or is this a desktop where you may not be able to tell?
 
If you think it could be heat related you can do an easy install of lm-sensors and use a terminal to check temps. If you don't like the terminal there are applets for various temperature monitors. 
```
sudo apt-get install lm-sensors
```That's LM-SENSORS in lower case, not an I or a 1. Once installed all you have to do is type the word sensors in a terminal for output of temps. Many systems approach critical between 90-110 degrees celcius. My systems are 99C or 100C where they automatically shut off. 
 
If the problem is heat related there are steps you can take to help lower the heat. What are you doing when the system shuts down? Web surfing, watching videos, etc?
might also be power shortfall, if the PSU is borderline too small.

---

### Post by shaquille on 2010-10-25
> **endotherm said:**
> just to clarify, does it shutdown gracefully as it should, or does it just die with a black screen, and straight to bios load?

yes it shuts down gracefully.

---

### Post by matt_symes on 2010-10-25
Hi

Have you tried it using a live cd? what happens then?

Kind regards

---

### Post by endotherm on 2010-10-25
> **shaquille said:**
> yes it shuts down gracefully.
ok, that kinda pushes us away from power and heat. 

look at dmesg.0.log in System->Administration->Log File Viewer 
and see if you see any error messages at the bottom of the log. try to make note of the time of a given shutdown, and check your Messags, Kern, and Syslog for evidence of an error.

---

