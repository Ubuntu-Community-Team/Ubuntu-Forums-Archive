---
title: "Gimp 2.8 floating object problem"
date: 2012-06-03
forum: General Help
---

### Post by GreatDanton on 2012-06-03
Hey!
Last week I installed Gimp 2.8 (using some website which help me to compile it), and I can say that it works fine. But then if I draw something and then select the thing I draw, when I move that selection the selection is not moving in real time, but with delay (it's not smooth).

I am pretty sure that's not because of my graphic card or computer, since my computer is not that bad (take a look at the signature). Graphic card drivers are also installed (take a look at the picture I provided) and operating system is up to date.


Does anybody know how to solve this, because if the selection is moving with delay then Gimp is useless for me.

And another question. Is Gimp 2.8 final release for Ubuntu or it's just in testing phase?

---

### Post by GreatDanton on 2012-06-08
Bump!

---

### Post by mcduck on 2012-06-08
Moving things defintiely works perfectly smoothly for me in Gimp 2.8, so if it's not your computer or graphics card it could be the packages you compiled...

Perhaps try using compiled packages from some PPA repository instead of compiling Gimp from source yourself?

```

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp
```

---

### Post by GreatDanton on 2012-06-08
Hey,
thanks for the answer. No I didn't compile source code, I used the same commands like you did. After that I reinstall Gimp (install it from the Ubuntu Software Center), but the problem still remains.

I am not sure if I describe my problem clear enough. So one more time. When I want to move something (for example something I drew) using rectangle selection, the border (selection) isn't moving when I move my mouse. After 1-2 seconds I am able to see selection again (on the place I drop it). Everything would be fine, but with that delay it's very hard to work and you are not precise, even if you are using precise pangolin :)

---

### Post by mcduck on 2012-06-09
Yes, I understood what you are trying to do, and it's working perfectly smoothly for me, using Gimp 2.8 from the repository I linked here.

If the packages you have are the same, then the next likely reason for such interface lag would be graphics card/drivers. I'd recommend checking again that the drivers are working correctly, and perhaps trying using more recent driver version...

I also missed your last question, the answer to that is that there is (and will never be) no official version of Gimp 2.8 for Ubuntu 12.04, since Gimp 2.8 was released too late to get included. The package you are using comes from a third-party repository. And 2.8 is a stable release.

edit: if you just need a way to get layers and things positioned exactly, perhaps try using the arrow keys on your keyboard for more precise movements?

---

### Post by GreatDanton on 2012-06-09
How can I try if drivers are working correctly?

I have installed them via system settings/additional drivers. However I cannot install post release updates (why?).
I also reinstalled drivers using this post :[http://ubuntuforums.org/showthread.php?t=1982640&highlight=how+i+install+ati+drivers](http://ubuntuforums.org/showthread.php?t=1982640&highlight=how+i+install+ati+drivers)

Today I was playing with AMD catalyst control center. I changed the Tear free, and set all sliders to maximum. It's little better but it's not perfect. Now the border of the floating object is always visible, but the picture is visible after 1 second (with delay).

I am pretty sure that the problem is with the drivers, since my graphic card is good enough to play games without any problems ( I have tested it when I had Windows).

Take a look at the first post (on picture)-There you can see which drivers I have enabled.

---

### Post by GreatDanton on 2012-06-13
bump

---

