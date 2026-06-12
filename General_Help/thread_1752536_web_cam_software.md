---
title: "web cam software"
date: 2011-05-07
forum: General Help
---

### Post by hunterkasy on 2011-05-07
I have a Logitech hd webcam c310, I am currently using it under xp as a security cam, by using the motion detection, and using the software that is provided by logitech.  I am having problems with the software working all the time and the scheduler does not work at all.  I would like to switch over to ubuntu instead of xp.  I know ubuntu detects the cam automatically. which is really nice. I am wondering what would be the best software to use,  all I want to use it for is the motion detection and to save the motion files to the hhd.  any idea's?

---

### Post by wolfen69 on 2011-05-07
**Motion** is a program that monitors the video signal from
one or more cameras and is able to detect if a significant
part of the picture has changed. Or in other words, it can
detect motion.

Motion is a command line based tool. It has no graphical
user interface. Everything is setup either via the
command line or via configuration files.

The output from motion can be:
   - jpg files
   - ppm format files
   - mpeg video sequences

Also, motion has its own minimalistic web server. Thus,
you can access the webcam output from motion via a browser.

You can download it via Synaptic Package Manager.

---

### Post by hunterkasy on 2011-05-08
> **wolfen69 said:**
> **Motion** is a program that monitors the video signal from
one or more cameras and is able to detect if a significant
part of the picture has changed. Or in other words, it can
detect motion.

Motion is a command line based tool. It has no graphical
user interface. Everything is setup either via the
command line or via configuration files.

The output from motion can be:
   - jpg files
   - ppm format files
   - mpeg video sequences

Also, motion has its own minimalistic web server. Thus,
you can access the webcam output from motion via a browser.

You can download it via Synaptic Package Manager.

thanks, I will take a look at it to see how easy it is to use

does anyone know of one that has a gui? for case this is to hard for me?

---

### Post by MODYSAMA on 2011-05-09
Hello everybody,
I need you knowledge, please.

In the configuration file of **[COLOR=Red]Motion[/COLOR]**.

[LIST]
[*] it's written in bash script language. Isn't it?
[*] I want to know, how is that file be interpreted! And Who responsible for that interpretation operation?
[*] Is that [COLOR=DarkSlateGray]**motion.conf**[/COLOR] linked to a specific libraries?
[/LIST]
***_e.g._*** 
> videodevice /dev/video0
> input 8

**videodevice /dev/video0** #How it know that mean listen to get an input for device video0?
**input 8** #How it know that means, the input is USB webcam ?
[I][B].
.
Please, I need a response, I am really in need to help.[/B][/I]

---

