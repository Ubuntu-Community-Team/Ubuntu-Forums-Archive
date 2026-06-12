---
title: "WTF I know going green is the new thing but this ain't gonna fly"
date: 2011-04-29
forum: General Help
---

### Post by JJake005 on 2011-04-29
I just got done upgrading to 11.04 and everything is green not a linux pro and i hope there is a quick fix please help

---

### Post by EarlsFurniture on 2011-04-29
hmm... everything in my Natty is still purple and orange.

---

### Post by Blasphemist on 2011-04-29
> **JJake005 said:**
> I just got done upgrading to 11.04 and everything is green not a linux pro and i hope there is a quick fix please help

Could you be more specific about what and when? We really need to know more to be able to offer anything.

---

### Post by JJake005 on 2011-04-29
Everything downloaded fine then after the restart insted of black ubuntu.... start screen it was green right from the get go im hooked up thru an hdmi cable to a new 55inch vizio with dell studio hybrid 2.16ghz t5850 core duo

---

### Post by matt_symes on 2011-04-29
Hi

Do you have some screen shots ?

Kind regards

---

### Post by Thewhistlingwind on 2011-04-29
Take a screenshot, post it. (In case you don't know, print screen key, or look in accessories.)

---

### Post by Blasphemist on 2011-04-29
We're getting closer to understanding but still need a bit more. Are your colors all wrong or just at the start of boot? Do you have any other monitor to try just to see if it has to do with the big visio? Does it seem to work but just have bad colors? Were the colors right when using try ubuntu from the cd? How about during the install? Have you looked at this as it shows the default color scheme?

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by JJake005 on 2011-04-29
well i hooked machine to hp w2207h in what do you know it works fine 10.10 worked perfect with vizio please let me know if i should reinstall it for now anyway no way I could operate on this 22 inch screen

---

### Post by JJake005 on 2011-04-29
oh yeah colors were wrong all the time not just at boot

---

### Post by Blasphemist on 2011-04-29
Does the system recognize your monitor correctly like mine shown in the screen shot? If not, try detect monitors. I'll keep looking.

---

### Post by jerome1232 on 2011-04-29
Screenshot?

It's been asked for several times. If you want help, you should respond to requests from those trying to help you.

---

### Post by tgm4883 on 2011-04-29
I'd just like to point out that a screenshot likely won't help. It would show correctly, but not how the OP is seeing it. 

@OP you will likely need to take a picture with your digital camera and post the pic. Also, how did you hook the PC up to your monitor?

---

### Post by JJake005 on 2011-04-29
thanks tgm and in response to Blasphemist it recognizes the vizio just fine as in your screenshot but its green all pics video everything black = supergreen

---

### Post by JJake005 on 2011-04-29
oh yeah i'm gonna go to sleep now if thats cool with you jerome

---

### Post by Blasphemist on 2011-04-29
So I'm wondering if tgm isn't onto something. What cable and connections are you using? Is it the same as you used for the little monitor (that's bigger than my big one :o)?

---

### Post by JJake005 on 2011-04-29
oh tgm i used hdmi to connect vizio also same to make it work with hp w2207h

---

### Post by tgm4883 on 2011-04-29
My next question is what video card, and are you using the proprietary graphics drivers?

---

### Post by matt_symes on 2011-04-30
Hi

> I'd just like to point out that a screenshot likely won't help. It would show correctly, but not how the OP is seeing it. 

@OP you will likely need to take a picture with your digital camera and post the pic. Also, how did you hook the PC up to your monitor?

That was exactly what i was trying to identify. Is it a monitor issue or some kind of video card issue. (or something else). If the screen shot is green then..

I do think you are right though. I would post both a screen shot and a picture.

Assumption is the mother of all %%6$£??*. That Crashed a probe on Mars (metric, imperial)

Gather as much info as possible for elimination, especially when diagnosing at a distance.

I don't expect the screen shots to be green either but until it's eliminated...

Kind regards

---

### Post by JJake005 on 2011-04-30
I'm going to upload a video on you tube for any of you to view today I'll start be booting the system then dose anyone have suggestions of what you you like to see done to troubleshoot in the video I don't know how to find what type of graphics card i have or if I'm running certain graphics drivers

---

### Post by bollix47 on 2011-04-30
As I had something similar happen to me a few years back I'll add my 2 cents for what it's worth.

My color problem turned out to be a bent pin in the monitor's plug which happened to be one that transmits color info to the monitor.  

Straightened out the pin and the colors were back to normal.;)

---

### Post by tgm4883 on 2011-04-30
> **bollix47 said:**
> As I had something similar happen to me a few years back I'll add my 2 cents for what it's worth.

My color problem turned out to be a bent pin in the monitor's plug which happened to be one that transmits color info to the monitor.  

Straightened out the pin and the colors were back to normal.;)

Heh, I have actually had that happen before. It sure is a PITA to diagnose.

---

### Post by jerome1232 on 2011-04-30
> **JJake005 said:**
> I'm going to upload a video on you tube for any of you to view today I'll start be booting the system then dose anyone have suggestions of what you you like to see done to troubleshoot in the video I don't know how to find what type of graphics card i have or if I'm running certain graphics drivers

To see what graphics card you have and the driver you are using post the output of the following.

Please enclose it in [noparse]```

```[/noparse] tags, you can do that by going into advanced edit mode and highlighting the text, and clicking the # button in your toolbar.

If you have an nvidia card you may just need to pop into the nvidia control panel and adjust the hue in there.

```
sudo lshw -C video
```

---

### Post by JJake005 on 2011-04-30
well I can't cut and paste the output from terminal and would not no where to find advanced edit options but here is you tube link for super green terminal output [http://www.youtube.com/watch?v=5xRoshB209w](http://www.youtube.com/watch?v=5xRoshB209w)

---

### Post by JJake005 on 2011-04-30
Oh here it is





jjake005@jjake005-Studio-Hybrid-140g:~$ sudo lshw -c video
[sudo] password for jjake005: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:fe600000-fe6fffff memory:d0000000-dfffffff ioport:c400(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe700000-fe7fffff
jjake005@jjake005-Studio-Hybrid-140g:~$

---

### Post by JJake005 on 2011-04-30
here is the boot 
[http://www.youtube.com/watch?v=JZ8snkpjWMM](http://www.youtube.com/watch?v=JZ8snkpjWMM)

---

### Post by Blasphemist on 2011-04-30
I see from the video that normal colors do display for icons and such. It looks like you are using a very green theme. Just saying that's what it looks like. Have you changed themes? Does that change this? I'm not surprised in some color difference from normal but this is extreme. Try other themes and let us know if it changes what you see at all. It looks like it changes when a driver loads during boot and that black is displaying as green.

---

### Post by mdshann on 2011-04-30
I have had my monitor go green when the DVI cable was knocked a little loose. Maybe the connection on the PC or on the TV is not right. Did you try another HDMI port on the TV?

---

### Post by Blasphemist on 2011-04-30
Check this out and see if you think its worth trying the method that isn't permanent but rather for just one boot. nomodeset and acpi_osi may have potential. Might be worth a try and what happens might help solve this even if they aren't the solution.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by JJake005 on 2011-05-01
well i put my 10.10 disk back in and installed alongside 11.04. then when i restarted and accidently choose the wrong partition what do you know 11.04 is in true color wtf

---

### Post by Blasphemist on 2011-05-01
I don't know whether to say sometimes you get lucky or unlucky :)

---

### Post by matt_symes on 2011-05-02
Hi

> start screen it was green right from the get go im hooked up thru an  hdmi cable to a new 55inch vizio with dell studio hybrid 2.16ghz t5850  core duoCan you connect up using another connector other than HDMI (if it has other connectors). 

It will help eliminate the obvious but it sounds very much like the HDMI green screen horror.

Kind regards

---

### Post by tgm4883 on 2011-05-02
> **JJake005 said:**
> well i put my 10.10 disk back in and installed alongside 11.04. then when i restarted and accidently choose the wrong partition what do you know 11.04 is in true color wtf

Please mark the thread as solved so people that have not read the whole thing stop posting solutions

---

### Post by cpitris on 2011-11-05
So ... The solution is to try and see if you get lucky with a 10.10  installation???!!!

I have the same problem and I sure hope there is a better solution than that!!! It's sad to see the problem persisting through 11.04 and 11.10 while everything worked fine in 10.10.

Please post if you have come across something.

---

### Post by uRock on 2011-11-05
Necromancy

Thread Closed

---

