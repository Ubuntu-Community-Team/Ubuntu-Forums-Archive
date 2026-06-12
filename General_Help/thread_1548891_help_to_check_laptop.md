---
title: "help to check laptop"
date: 2010-08-09
forum: General Help
---

### Post by natholas on 2010-08-09
Hey everyone, i am about to order a dell studio 17 and i would like to set up a duel boot with windows 7/ubuntu i would like to know if anyone else has this laptop or knows how well it will work

(im getting the one with the i7 1.6ghz and an ati radeon graphics card and touch screen.. i have no idea if that will work but it doesnt matter too much if the touch screen doesnt work in ubuntu)

thanks very much in advanced :D

---

### Post by inameiname on 2010-08-09
I'm not sure, but I just want to let you know of something that's been going around on here about i5s and i7s computers, that those core won't work well with the kernel Lucid has, 2.6.32, as only the later kernels will work well with it. I think I read it was not until the most recent one, 2.6.35, that Ubuntu works alright. So do some research. And in the event that you require the latest kernel, it's very easy to install:

This is all you have to do:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

Then if it works, sweet. If not, you can revert back to your older  kernel. Just look into how, usually by restarting and hitting 'Shift'  button so it shows the boot menu, which will show which kernel you want  the computer to boot with. And when you boot with your current one,  2.6.32-24-generic, you can remove the 2.6.35 one:

sudo apt-get remove --purge 2.6.35-14-*

Here is a thread I found real quick on here on a few of the issues with the i3, i5, i7 processors and Lucid's kernel:

[http://ubuntuforums.org/showthread.php?t=1395454](http://ubuntuforums.org/showthread.php?t=1395454)

---

### Post by Woody1987 on 2010-08-09
I have had a dell studio 17 and everything worked with ubuntu, although it didn't come with a touch screen.

---

### Post by natholas on 2010-08-09
cool. thanks guys.. ill look into the kernel problem.. ill just download the latest version from ubuntu.org.. that should be the latest then right?

edit. thanks woody :) thats good to know

oh and btw.. is anyone using blender 3d with this laptop? ubuntu or windows 7? thats the main reason im getting a quad core laptop :P i posted a there but they are not as fast to reply as u guys :P

---

### Post by inameiname on 2010-08-09
I'm afraid not. In Ubuntu Lucid, the latest that is currently available is 2.6.32-24. It started out as 2.6.32-21, and it won't update past 2.6.32 in this release.  Maverick's Alpha 3 does have the latest kernel, 2.6.35-14, though. Thus, if you want Lucid to have the latest kernel, you must either use that PPA or get them here, [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and download and install them manually, which is essentially the same.

---

### Post by natholas on 2010-08-09
ok thanks, i will do that once i get the laptop :D im pretty exited as u can imagine as the first and only laptop i have ever had has been an asus 900a running ubuntu.. its been really great (even doing 3d animation) but its time to upgrade.. big time :P

---

### Post by inameiname on 2010-08-09
Hehe. My first laptop is my current one, and it's three years old now. And after having used Ubuntu and Linux for over a year now, I'm psyched for a new fancier one, so I can unleash all that Linux actually has to offer. Enjoy.

Oh, and before I forget, depending on how long before you get your new laptop, remember to do a search through Synaptic, or through the terminal using 'sudo apt-cache search linux-image', because the latest kernel version I put in that terminal code might not be the latest then, and thus, you must change it to the latest, as only the latest would be available from that PPA.

---

### Post by Bachstelze on 2010-08-09
inameiname, stop spreading FUD.  Lucid will work just fine on an i5/7.

---

### Post by inameiname on 2010-08-09
Wow. I'm only sharing what I've heard, and read on here about the cores and Ubuntu. Just giving a comment, that is all. Doesn't mean it's a fact that no i5 or i7 will work.

---

### Post by natholas on 2010-08-09
> **Bachstelze said:**
> inameiname, stop spreading FUD.  Lucid will work just fine on an i5/7.

thanks :) that would not have been a big problem anyway.. im used to fixing little things like that.. i was hoping there wasent going to be something like.. oh the touch screen will mess up ubuntu.. or that graphics card wont work.. stuff like that :P im probably going to mess with different kernels anyway :) 

thanks allot guys :) all the input is greatly appreciated.. i would have hated to not being able to run ubuntu on my new laptop.. u have to use something when windows gets sick.. :P

---

### Post by inameiname on 2010-08-09
Ah, that's cool. Yeah, there always seems to be something with any and all computers and you have to tweak this and/or that. :P Hopefully you won't have too many troubles. Good luck!

---

