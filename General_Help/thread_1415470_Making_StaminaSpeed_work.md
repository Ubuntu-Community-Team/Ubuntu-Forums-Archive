---
title: "Making Stamina/Speed work"
date: 2010-02-24
forum: General Help
---

### Post by christia on 2010-02-24
Hi All
 
I would like to solve the following issue, which is the last functional point in which Ubuntu doesn't work.
 
I have a Sony Vaio Z, VGN-Z540 to be precise. It has a stamina/speed button, which currently doesn't work. I would like to make that happen.
 
I've done a lot of research on this - it seems like a lot of people have experienced this problem but haven't been able to solve it. the majority of the people who have this problem is people using Windows 7, so thought an extra motivation to solve this could be the possibility to show Windonites that Ubuntu is better at solving problems like this ;-)
 
The blog-link in the bottom seems to address this for ubuntu. I am not capable of following what is going on in entirety, but as far as i understand there are two graphics cards in my computer, an intel and an nvidia, and the button switches back and forth between those. 
 
If anyone has the time and patience to do so, i would like him/her to help with explaining me how to make this work in stupido language (as i am, hands down, a linux stupido). i wasn't able to make it work in windows7 either before i swapped.
 
I am using 10.04 - not sure if that makes a difference. i really like this install (works a lot better than 9.04 did), so would like to keep it! 
 
Anyone?
 
Blog-link
[http://global-social.net/tiki-view_blog.php?blogId=3](http://global-social.net/tiki-view_blog.php?blogId=3)

---

### Post by bruno9779 on 2010-02-24
You could divide this in separate tasks, then make a script.

1. go to system > Preferences > Keyboard shortcut, and try and see what is the key detected as (and if it is detected at all
2. find out how to enable, disable nvidia card
3. find out how to enable, disable intel card

4. now you need to put all this info together in a bash script. People here can help, but this is point 4 ...

---

### Post by 3rdalbum on 2010-02-24
Support for this is in development on the Linux side, and currently requires the X server to be restarted. My understanding is that this is similar to the way Windows does it, requiring all programs to be closed.

You may be able to find an svn repository that contains the testing code for this, but it won't be user-friendly and might not work at all. It would also involve compiling this code from source.

It's a pretty exotic feature, after all, with a dubious benefit-to-effort ratio.

---

### Post by christia on 2010-02-25
Ok. the benefit: the nvidia graphic card is better, and right now i am not using it at all - not optimal imo. but if it is so difficult, i will hold off. funny that everything nonstandard is always a superbig hazzle in linux :)

---

### Post by amortvigil on 2010-03-31
what i found out is:

the switch enables / de activates (switches) the video cards

I found something : [http://global-social.net/sony-VGN-Zseries](http://global-social.net/sony-VGN-Zseries)
and i found: [http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html)

i tried ariels method with my specs and cards but as xorg.conf got pasted with the current mode i had to delete it to load the new mode.

any progress on your sides??

---

