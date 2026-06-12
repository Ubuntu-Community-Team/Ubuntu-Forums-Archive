---
title: "Webcam doesn't work with Skype"
date: 2010-01-30
forum: General Help
---

### Post by Coco999 on 2010-01-30
I have difficulty with my webcam and Skype. I can see the other person but she can't see me. From a previous thread:

> Are you sure your camera isnt working? Supported hardware drivers are in the kernel usually.
Test: press alt+f2, type gstreamer-properties go to the video tab and see if your camera is listed as a device. If yes, press the test button.

This test was OK. I could see my face on the screen.


> Ah, the Skype camera thing...

Launch it this way:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I tried this. It launches Skype OK, but the little window that should show what my webcam sees, appears full of black and white static.

What can I do? Thank you very much for your help.

---

### Post by Coco999 on 2010-01-31
Can somebody help me, please?

---

### Post by no2498 on 2010-01-31
get a program like (cheese and wxcam)
open a terminal type (gstreamer-properties)click enter
click video try v4l1 or v4l2 click the bottom test
cam comes up in a small window

play with it till it comes on


now open cheese or wxcam 
you may need to play with the settings
hope this helps

---

### Post by amac777 on 2010-01-31
Try launching skype this way:

```
skype-with-v4l
```

And then check if your camera works with skype.

---

### Post by marin123 on 2010-01-31
if all of the above does not work, you can install skype from medibuntu, thats how i got mine working (but first sudo apt-get remove skype)...

[http://adria.fesb.hr/~mbareta/skype](http://adria.fesb.hr/~mbareta/skype)

---

### Post by Coco999 on 2010-01-31
> get a program like (cheese and wxcam)
open a terminal type (gstreamer-properties)click enter
click video try v4l1 or v4l2 click the bottom test
cam comes up in a small window
I did this and saw my face on the screen OK. I don't see the point of any adjustments under cheese, since the image was perfect. It is the connection with Skype that fails.

```
coco@coco-desktop:~$ skype-with-v4l
skype-with-v4l: command not found
coco@coco-desktop:~$ 
```
This is what I got. In my original thread message, I tried something similar but failed.

> if all of the above does not work, you can install skype from medibuntu, thats how i got mine working (but first sudo apt-get remove skype)...
Any reason at all why this should work? I have the latest Skype. Is the version in medibuntu doctored in any way?

---

### Post by marin123 on 2010-02-01
medibuntu version installes 6 additional packages...
i tried installing from skype.com and didnt work.. with this debs everything worked out of the box...

---

### Post by Coco999 on 2010-02-01
> medibuntu version installes 6 additional packages...
i tried installing from skype.com and didnt work.. with this debs everything worked out of the box...

I can't find Skype in Medibuntu. This is what I did. I went to Medibuntu website and copied this to a terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then I copied this:
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```

I expected to see now many packages added to the usual repository, including Skype, but nothing of this sort happens.
How do I find Skype in medibuntu?

---

### Post by marin123 on 2010-02-01
> **marin123 said:**
> if all of the above does not work, you can install skype from medibuntu, thats how i got mine working (but first sudo apt-get remove skype)... 

[http://adria.fesb.hr/~mbareta/skype](http://adria.fesb.hr/~mbareta/skype)

i already gave you a link to my college server...

---

### Post by Coco999 on 2010-02-01
Sorry, the link to your college server did not appear at your original message, strange as it is. 
I found this:
	> Parent Directory	 	 -
[ ]	skype-common_2.1.0.47-0medibuntu0.9.04.1_all.deb
[ ]	skype-common_2.1.0.47-0medibuntu2_all.deb	
[ ]	skype_2.1.0.47-0medibuntu2_amd64.deb	
[ ]	skype_2.1.0.47-0medibuntu2_i386.deb	

I need    skype_2.1.0.47-0medibuntu2_i386.deb

Do I have to install as well    skype-common_2.1.0.47-0medibuntu2_all.deb?

Thank you very much for your help.

---

### Post by marin123 on 2010-02-01
try installing just skype i386, if all dependencies arent satisfied then download both skype-common debs and install (i guess i dont have to mention you have to install common debs first ;) )...
hope it works for you...

p.s. i put this files on my server because medibuntu no longer provides these packages, but this worked for me and a few more people, so i decided to keep it somewhere safe :)

---

### Post by Coco999 on 2010-02-02
> **no2498 said:**
> get a program like (cheese and wxcam)
open a terminal type (gstreamer-properties)click enter
click video try v4l1 or v4l2 click the bottom test
cam comes up in a small window

play with it till it comes on


now open cheese or wxcam 
you may need to play with the settings
hope this helps

I did this. With the button test I see my face on the screen. But with cheese I get only a window full of white and black static like image, with some pattern to it consisting in vertical bands.

> you may need to play with the settings
What settings? I saw none available.
I think I ought to fix this before trying further reinstallations of Skype.

---

### Post by no2498 on 2010-02-02
in cheese click preference edit try a smaller size

288x -- is all it lets me use

---

### Post by Coco999 on 2010-02-04
As advised, I tried to install 
[ ] skype_2.1.0.47-0medibuntu2_i386.deb 

It told me that dependancies were not satisfied, so I installed first [ ] skype-common_2.1.0.47-0medibuntu2_all.deb

Then the installation could proceed, but I got an error message:
> Error: Rompe el paquete existente 'skype' conflicto: skype ( )
Meaning: it breaks the existing package 'skype' conflict: skype

However, the installation was performed and I could start the program. The person whom I talk to was not connected, so I could not see whether skype accepts the webcam. I think there is a procedure to test this without connecting with somebody else, but could not find it-

---

### Post by marin123 on 2010-02-04
> **Coco999 said:**
> As advised, I tried to install 
[ ] skype_2.1.0.47-0medibuntu2_i386.deb 

It told me that dependancies were not satisfied, so I installed first [ ] skype-common_2.1.0.47-0medibuntu2_all.deb

Then the installation could proceed, but I got an error message:

Meaning: it breaks the existing package 'skype' conflict: skype

However, the installation was performed and I could start the program. The person whom I talk to was not connected, so I could not see whether skype accepts the webcam. I think there is a procedure to test this without connecting with somebody else, but could not find it-

i will write it again:
before installing skype medibuntu debs, open terminal and type in:
```
sudo apt-get remove skype
```
then it will install normally...
there is an option for testing video in Options -> Video Devices

---

### Post by Coco999 on 2010-02-04
Thank you for your reply. 

First of all let me tell you that before installing your medibuntu skype, I had run the following:
```
sudo apt-get purge skype skype-*
``` which seems to be a little more general than your remove skype command.
Under these conditions (i.e.; both common medibuntu and medibuntu installed) I launched skype and tested the camera through options as you told me. I got only a black and white statics, with a certain sinusoidal pattern, fast moving.

Now I ran yours and installed only the medibuntu skype deb alone. It was accepted. I launch skype but can't start a session. It tells me: Failure starting session, maybe there is another instance.

At the risk of seeming a little dense, I will ask 2 questions:
1. How do I know what is installed?
2. How do I know what is running?

By now, the thing is driving me mad. But I'm determined to solve it, so thank you for the hand you are giving me.

Regards.

---

### Post by marin123 on 2010-02-04
1. & 2. I don't know :(

my advice: search for skype on your computer and delete everything (except debs you will install)...
i think skype doesnt go away completely when you uninstall it...

---

### Post by Coco999 on 2010-02-05
marin123

Thank you for your help and your patience. I think I have now solved the problem. I removed skype and reinstalled common medibuntu and medibuntu. The problem was that I have as well another video device, a TV tuner card, that was taken as default by skype. In the test window, I had to choose the webcam instead, click apply, close the window, and start again the test. Then I could see my image. I trust it will be OK in an actual communication, but my friend will be away from home for a few days.
I'll mark the thread as solved.

---

