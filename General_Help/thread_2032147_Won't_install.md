---
title: "Won't install?"
date: 2012-07-23
forum: General Help
---

### Post by Fireoath on 2012-07-23
Sup, I'm Fireoath.

Alright so lets just start off with my laptop that i am trying to install Ubuntu on.

Laptop
------
Dell
Inspiron 1300
Intel Celeron M
32 Bit.

So, I decided to get Ubuntu obviously, the 12.04(32Bit) desktop on my laptop. I put the ISO image on a CD and I made my USB key (4gbs) boot able also, when I put in the disk, it goes to the Ubuntu screen where it has 5 dots below it, when loading that it freezes and no matter how long you wait it doesn't go anywhere at all. So after repeating this about 10-15 times i formatted the computer using the CD I had before. I decided to use the boot able USB, so I plug it in, restart the computer pressed F12, blah blah blah, and so we got back to the same screen and the same problem keeps occurring, i repeatedly kept trying over +10 times and it wouldn't change. 

Can someone help me?

If you have any questions feel free to comment.

---

### Post by mastablasta on 2012-07-23
you didnt' post any system specs besides the CPU. 
 
what GPU do you have? how much RAM do you have? did you try any of the boot options ? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
did you wait long enough? it might take a while for liveCD to load as everyhting has to be loaded to ram first. you can press Esc key to see if there is any error messages below that screen.

---

### Post by TheFu on 2012-07-23
Google found this: 
* [http://askubuntu.com/questions/130262/dell-inspiron-1300-hangup-during-boot](http://askubuntu.com/questions/130262/dell-inspiron-1300-hangup-during-boot) with a solution
* [http://askubuntu.com/questions/161616/ubuntu-install-cd-hangs-at-5-red-dots-while-booting](http://askubuntu.com/questions/161616/ubuntu-install-cd-hangs-at-5-red-dots-while-booting) for more details

---

### Post by Fireoath on 2012-07-23
> **mastablasta said:**
> you didnt' post any system specs besides the CPU. 
 
what GPU do you have? how much RAM do you have? did you try any of the boot options ? : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
did you wait long enough? it might take a while for liveCD to load as everyhting has to be loaded to ram first. you can press Esc key to see if there is any error messages below that screen.

Intel 915 GM/910GNK Graphics
Video Memory 8 mb
1.60 Ghz
512 MB
400 Mhz

I waited long trust me. I'll try the boot options lets hope it atleast works.

---

### Post by uylug on 2012-07-23
I'd try using a DVD. I've seen weird things happen with USB dongles.

Ubuntu should definitely run on your hardware.

---

### Post by Fireoath on 2012-07-23
I'll try burning it on another cd and try the installation again. lets hope it works..

---

### Post by Fireoath on 2012-07-23
Alright so, I tried to install it using a newly burned Disc and i got this... someone help me? I don't know what to do now, explain in detail please.

---

### Post by Fireoath on 2012-07-24
No help?

---

### Post by lincoln32 on 2012-07-24
the error is just to tell you that it cannot find a good driver for your wifi card continue/ignore then once you are done it can be fixed
I have several broadcom B4300 and there are several differnt drivers to try but it can does and will work in wireless:D

---

### Post by mastablasta on 2012-07-24
> **Fireoath said:**
> Intel 915 GM/910GNK Graphics
Video Memory 8 mb
1.60 Ghz
512 MB
400 Mhz
 
I waited long trust me. I'll try the boot options lets hope it atleast works.
 
for this kind of mashcine i suggest Xubuntu (or perhaps even lubuntu). if it works well you can add Ubuntu to it and then try to switch to it.
 
Unity uses hardware acceleration and your card is really weak.
 
you might also need to use nomodeset boot option with that chip. try running it live firts.
 
as mentioned error message is that driver for WI-fi is not part of kernel. once you get it installed you can try to start solving it (maybe it's enough just to connect with wired connection to intenet and a message will popup to install the drivers).

---

### Post by Fireoath on 2012-07-24
> **mastablasta said:**
> for this kind of mashcine i suggest Xubuntu (or perhaps even lubuntu). if it works well you can add Ubuntu to it and then try to switch to it.
 
Unity uses hardware acceleration and your card is really weak.
 
you might also need to use nomodeset boot option with that chip. try running it live firts.
 
as mentioned error message is that driver for WI-fi is not part of kernel. once you get it installed you can try to start solving it (maybe it's enough just to connect with wired connection to intenet and a message will popup to install the drivers).

May I ask where do i find Xubuntu / lubuntu and are they equal to ubuntu, worse or better?

---

### Post by Fireoath on 2012-07-24
> **mastablasta said:**
> for this kind of mashcine i suggest Xubuntu (or perhaps even lubuntu). if it works well you can add Ubuntu to it and then try to switch to it.
 
Unity uses hardware acceleration and your card is really weak.
 
you might also need to use nomodeset boot option with that chip. try running it live firts.
 
as mentioned error message is that driver for WI-fi is not part of kernel. once you get it installed you can try to start solving it (maybe it's enough just to connect with wired connection to intenet and a message will popup to install the drivers).

I've found Lubuntu, and decided to get it, i'll let you know if it works. Thank you for the help so far and continue to guide me please.

---

### Post by dino99 on 2012-07-24
here you get the required links and how to do installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

and maybe posting into the Dell subforum is a better place too :P

---

### Post by oscarivera9 on 2012-07-24
> **mastablasta said:**
> for this kind of mashcine i suggest Xubuntu (or perhaps even lubuntu). if it works well you can add Ubuntu to it and then try to switch to it.
 
Unity uses hardware acceleration and your card is really weak.
 
you might also need to use nomodeset boot option with that chip. try running it live firts.
 
as mentioned error message is that driver for WI-fi is not part of kernel. once you get it installed you can try to start solving it (maybe it's enough just to connect with wired connection to intenet and a message will popup to install the drivers).

I agree on using Xubuntu, or Lubuntu.  I had a similar problem with a desktop and I tried Xubuntu and it worked like a charm. 
Also, try a wired connection, that should help if you're still having the same wifi problems.  Or you can plug in one of those usb wireless cards just for the installation (I had to do that once for a friend's laptop), then after installation you can download the correct driver for you laptop's wifi card.

---

### Post by Fireoath on 2012-07-24
> **oscarivera9 said:**
> I agree on using Xubuntu, or Lubuntu.  I had a similar problem with a desktop and I tried Xubuntu and it worked like a charm. 
Also, try a wired connection, that should help if you're still having the same wifi problems.  Or you can plug in one of those usb wireless cards just for the installation (I had to do that once for a friend's laptop), then after installation you can download the correct driver for you laptop's wifi card.

I have the drivers on a seperate usb, but the computer was formatted, not sure if it had anything to do with why this "drivers" problem is occurring but i'm going to install it once xubuntu / lubuntu installs or if it does at all. I feel you guys may be thinking I am asking questions on the same laptop i am installing ubuntu on, To clear it all up, no I am using my pc and my other 2 laptops.

Question - Lubuntu Or Xubuntu? which one would you guys recommend and which do you think is better or are they basically the same thing?

---

### Post by oscarivera9 on 2012-07-24
> **Fireoath said:**
> I have the drivers on a seperate usb, but the computer was formatted, not sure if it had anything to do with why this "drivers" problem is occurring but i'm going to install it once xubuntu / lubuntu installs or if it does at all. I feel you guys may be thinking I am asking questions on the same laptop i am installing ubuntu on, To clear it all up, no I am using my pc and my other 2 laptops.

Question - Lubuntu Or Xubuntu? which one would you guys recommend and which do you think is better or are they basically the same thing?

Don't worry, at least I don't think it matters which laptop you're using and/or which one you're having problems with.  What really matters here is that you get the help you need.

To answer your question about which one I recommend or if they're basically the same thing, the best answer is this:
Try them both out with a Live CD or Live DVD, that's the beauty of using a Live CD, you can try it out before you commit to installing it (something you can never do with Window$).  To me, both Lubuntu and Xubuntu are pretty much the same, at least when compared to Ubuntu or Kubuntu.
 The difference, primarily, is in the desktop environment that they use.   It would be too hard for me to describe what the differences between all of them are, it's kind of one of those things that you have to see for yourself.  However, underneath it all, it's all really Ubuntu, no matter which one you look at, they're all like brothers in a way.

  It all really boils down to preference, so yet again I encourage you to try out different ones from a Live CD.
 With Lubuntu and Xubuntu, much like Ubuntu, after you put in the CD and get it to boot, it will ask you if you want to "try" it or "install" it; at this point choose the "try" option and check it out.  Then reboot, take out the disc, put in the other one from a different distribution and again after it boots, select "try", then you'll know for yourself which one you like best.  You be the judge.

My preference, by the way is:
1.** Ubuntu**
2. Ubuntu Studio (which feels like Xubuntu)
3.** Xubuntu**
4. Fedora (this one is completely different from the others as it's not from the Ubuntu family)

---

### Post by Fireoath on 2012-07-24
> **oscarivera9 said:**
> Don't worry, at least I don't think it matters which laptop you're using and/or which one you're having problems with.  What really matters here is that you get the help you need.

To answer your question about which one I recommend or if they're basically the same thing, the best answer is this:
Try them both out with a Live CD or Live DVD, that's the beauty of using a Live CD, you can try it out before you commit to installing it (something you can never do with Window$).  To me, both Lubuntu and Xubuntu are pretty much the same, at least when compared to Ubuntu or Kubuntu.
 The difference, primarily, is in the desktop environment that they use.   It would be too hard for me to describe what the differences between all of them are, it's kind of one of those things that you have to see for yourself.  However, underneath it all, it's all really Ubuntu, no matter which one you look at, they're all like brothers in a way.

  It all really boils down to preference, so yet again I encourage you to try out different ones from a Live CD.
 With Lubuntu and Xubuntu, much like Ubuntu, after you put in the CD and get it to boot, it will ask you if you want to "try" it or "install" it; at this point choose the "try" option and check it out.  Then reboot, take out the disc, put in the other one from a different distribution and again after it boots, select "try", then you'll know for yourself which one you like best.  You be the judge.

My preference, by the way is:
1.** Ubuntu**
2. Ubuntu Studio (which feels like Xubuntu)
3.** Xubuntu**
4. Fedora (this one is completely different from the others as it's not from the Ubuntu family)

Even the "try it" before installing doesn't work, I do not have any blank dvd's therefore I am using a 4gb usb key and when i tried to install Lubuntu it still froze... I'm going to download Xubuntu and try to install it using the usb...

---

### Post by muteXe on 2012-07-24
Has anyone mentioned verifying the md5 checksum of your iso download?

[https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

It doesn't like a corrupt download, but it doesn't hurt to check.

---

### Post by Fireoath on 2012-07-24
> **muteXe said:**
> Has anyone mentioned verifying the md5 checksum of your iso download?

[https://help.ubuntu.com/community/HowToMD5SUM/](https://help.ubuntu.com/community/HowToMD5SUM/)

It doesn't like a corrupt download, but it doesn't hurt to check.

I've already done that.

Putting Xubuntu on my usb now.

Edit - Xubuntu freeze's also, whats going on? :/

---

### Post by mastablasta on 2012-07-24
> **Fireoath said:**
>  
Edit - Xubuntu freeze's also, whats going on? :/
 
did you use the boot options? and if so which ones did you try?

---

### Post by Fireoath on 2012-07-24
> **mastablasta said:**
> did you use the boot options? and if so which ones did you try?

What boot options? All I did was press F12 at the beginning, went to the usb ones and then clicked install xubuntu once the screen loaded up and it froze :/

---

### Post by mastablasta on 2012-07-25
read more here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

when it boots before you click install or try it there should be boot options (press F6 i believe)

---

### Post by Fireoath on 2012-07-27
> **mastablasta said:**
> read more here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

when it boots before you click install or try it there should be boot options (press F6 i believe)

I still dont understand

---

