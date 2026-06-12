---
title: "Ubuntu 12.04 insanely distorted text."
date: 2012-06-29
forum: General Help
---

### Post by matiic on 2012-06-29
Hi.

Not long ago, I upgraded to Ubuntu 12.04.
I've had a problem with the text going *really* weird and distorted. I have no idea what could be causing the problem at the moment.

Here are some screenshots to show what I mean:
[[img]http://s17.postimage.org/brhunr1az/Screenshot_from_2012_06_29_20_31_56.png[/img]](http://postimage.org/)

[[img]http://s17.postimage.org/re9414f2z/Screenshot_from_2012_06_29_20_32_29.png[/img]](http://postimage.org/image/re9414f2z/)

[[img]http://s17.postimage.org/y5zj3z42j/Screenshot_from_2012_06_29_20_32_46.png[/img]](http://postimage.org/)

If anyone could help, or has had the same problem, that would be great! I'm just going to restart my computer to get rid of the problem so that I can find out my specs. :)

---

### Post by matiic on 2012-06-29
Alright, this is the info that hardinfo gives:

-Computer-
Processor		: 2x Intel(R) Pentium(R) 4 CPU 3.20GHz
Memory			: 1015MB (472MB used)
Operating System	: Ubuntu 12.04 LTS

-Display-
Resolution		: 1280x1024 pixels
OpenGL Renderer		: Unknown
X11 Vendor		: The X.Org Foundation

---

### Post by matiic on 2012-07-09
bump

---

### Post by Bradford1040 on 2012-07-11
BUMP!!!! I have this issue or something like it, I have been looking and looking and.... looking and nothing, all I find is brand new posts like this with no fix or even a reply on some. I am still going to look of coarse and if I find something I promise to post back my results!


perfect example of my problem was taken by someone else but this is the same thing I am looking at

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1007906/+attachment/3173112/+files/Screenshot%20from%202012-06-02%2018%3A22%3A50.png](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1007906/+attachment/3173112/+files/Screenshot%20from%202012-06-02%2018%3A22%3A50.png)

this one as well same person 

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1007906/+attachment/3173113/+files/Screenshot%20from%202012-06-02%2018%3A23%3A17.png](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1007906/+attachment/3173113/+files/Screenshot%20from%202012-06-02%2018%3A23%3A17.png)

---

### Post by matiic on 2012-07-13
That's weird.
My problem is slightly different to yours (it doesn't look like that), so I don't know if they're related or not.
Either way, post back if you find something. I'll do the same.

---

### Post by Bradford1040 on 2012-07-13
Yeah I will, it seems there are more and more about this popping up but no one has a fix yet! But I will keep in touch if I find anything even if our problems are different! Good luck and hope all is well outside the PC world

---

### Post by vaxius on 2012-12-09
Same here, except it only happens to the number 5, and not every time. For example, I see a 5 on one of my chrome tabs that look fine, but if I click the time to look at my calendar, all the 5s are messed up.

I took a screenshot to illustrate.

---

### Post by Starfleet on 2012-12-09
Guys, not sure if this will all of you but it's worth a try. I have seen this on several machines that I recently upgraded to 12.04 from 10.04, all clean installs rather than an upgrade from within the system. All the machines were different and all were desktops with Nvidea onboard grahics...except one HP machine with a fitted Nvidea card, which also failed to boot until I sorted the driver. The problems were distorted on screen grahics or text just like the picture above in the original OP's post. 

The way I sorted it was to install the proper drivers following instructions from here: [http://*********************.com/2012/11/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://*********************.com/2012/11/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

You will need to scroll down the page, which is a **debian wordpress To do list for 12.04**, to the section on video drivers. It's not an onerous task and they make it very easy to follow. It's just copy and paste and you can trust the site. It has very precise video driver instructions to remove and install the proper drivers for your system which will likely fix your issues. It could also be other software issues I guess but I think it's driver related in view of my own experiences. It worked in everycase for me. Please try it and report back as soon as you can so everyone can benefit from your experiences. Hopefully, you'll all be fine. Good luck!

---

### Post by Impavidus on 2012-12-09
The 5s in your calendar are pixel maps stored somewhere in your video memory. The 5s in your browser too, but they are stored there by a different program and belong to a different font, so they they are a different object in video memory. It appears the first 5s were somehow corrupted. This indicates problem with your graphics driver, so I agree with the previous answer.

By the way, these errors often show up differently in screen schots compared to the actual screen.

---

