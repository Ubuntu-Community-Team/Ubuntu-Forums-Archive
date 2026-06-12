---
title: "Ubuntu hangs during boot"
date: 2009-09-06
forum: General Help
---

### Post by marc1uk on 2009-09-06
After making some hardware changes to my PC (new HD, gfx card), Ubuntu has started hanging for a long time (5-10mins) during boot. It pauses on the loading bar, then eventually drops to text, runs a few lines (no errors, loading kernel , restricted drivers etc.) then starts normally. Then everything seems fine. A fresh reinstall doesn't seem to have solved the problem.  Any ideas what might be causing this?

---

### Post by blazemore on 2009-09-06
Well you can install Bootchart:
```
sudo apt-get install bootchart
```

There's an article on Linux.com:
[http://www.linux.com/archive/feature/151496](http://www.linux.com/archive/feature/151496)

Post the resultant chart here, and someone (cleverer than me) will help pinpoint the problem (and solution).
All I know is that Bootchart is a great place to start!

---

### Post by scragar on 2009-09-06
And could you please upload the errors log?
You can find it in **/var/log/errors.log**

---

### Post by Barafu Albino Cheetah on 2009-09-06
You have some kernel modules installed that now look in vain for thier belowed hardware. Reinstall kernel, do an fsck of boot and root partitions, and all should be fine.

---

### Post by marc1uk on 2009-09-06
> **scragar said:**
> And could you please upload the errors log?
You can find it in **/var/log/errors.log**
Um, can't find that file. I've got a few logs (syslog, syslog.0, faillog, messages) but no error.log?

---

### Post by marc1uk on 2009-09-06
> **Barafu Albino Cheetah said:**
> You have some kernel modules installed that now look in vain for thier belowed hardware. Reinstall kernel, do an fsck of boot and root partitions, and all should be fine.
Sounds good, let's hope this works. Just looking for the kernel package number, 
```
 sudo apt-get --reinstall linux-image-2.6.12-9-386
``` is giving me
```
 Some Error. (C&P in terminal fail. Should've proof read)
```. goooogling... :9   

Edit: RIGHT. Gave up on that, used synaptic. Alas, no fix though. Removing the splash option from the boot parameters, the stall seems to be occurring after a series of codec errors: ```
codec_read: codec 0 is not valid
``` I've googled this, but found little that seem to be solved, and all seem to be with sound issues. My sound's working fine though..

---

### Post by marc1uk on 2009-09-06
> **blazemore said:**
> Well you can install Bootchart:
```
sudo apt-get install bootchart
```There's an article on Linux.com:
[http://www.linux.com/archive/feature/151496](http://www.linux.com/archive/feature/151496)

Post the resultant chart here, and someone (cleverer than me) will help pinpoint the problem (and solution).
All I know is that Bootchart is a great place to start!

Thanks for the tip, I'll give these two a go and if no luck, get that and see if it can shed any light. (probably keep it bookmarked too, this is always happening!)

---

### Post by marc1uk on 2009-09-06
[COLOR=White]b[/COLOR]u
b mp.

Downloading Bootchart atm. This thing's huge. Post back with results.

---

### Post by blazemore on 2009-09-06
Please don't bump after just one hour.
Post your bootchart; that's all I'm waiting for!

---

### Post by marc1uk on 2009-09-06
> **blazemore said:**
> Please don't bump after just one hour.
Post your bootchart; that's all I'm waiting for!
Sorry, been at this all day, getting impatient ^ ^;. I also usualy include more information (stuff I've tried, all dead ends) and get no responses, and no conclusion. In this case I've already tried reinstalling, even that didn't fix it. Without any help, it's... buy a new HD i guess?

Anyway! Bootchart is ... aloof. Installed the program but can't find it anywhere, so i ran 'bootchart' in terminal, and got: 
```
marc@HAL:~$ bootchart
Parsing /var/log/bootchart
06-Sep-2009 21:36:00 org.bootchart.Main render
WARNING: Unknown log file: HAL-jaunty-20090906-1.png
06-Sep-2009 21:36:00 org.bootchart.Main render
WARNING: Unknown log file: HAL-jaunty-20090906-1.tgz
06-Sep-2009 21:36:00 org.bootchart.Main render
WARNING: No process samples
Wrote image: ./bootchart.png
marc@HAL:~$ 
```Something not quite right there, and unfortunately I suspect with the chart also, which is attached. Not much use. :\ 
Could reboot and try again... it'll take 15 mins, but, no rush I suppose.
  
Edit: Aha!! Did a search for the HAL-jaunty-20090906.png, and that seems to be a proper bootchart! Attatched.

---

### Post by marc1uk on 2009-09-08
Need a sage on these, don't wanna bump the thread except to say thanks to the guys who offered their time and help - the problem seems to have solved itself! Honestly, I don't know what to say. 
I needed to print off my CV for a job application, which was on my old PC (has SATA drives that I couldn't transfer). After swapping everything back, printing the CV, then swapping it all back again, I just booted the problematic PC... and it fired up in seconds. 
I'll add a bootchart, just in case there's something in it that'll help others with the same problem later. Always feel a little unsettled leaving the problem as a mystery, but ... all's well that ends well i suppose? 

Thanks again to all those who offered help. You're the people who stop me formatting and going back to windows whenever this stuff comes up. Kudos. :KS

---

