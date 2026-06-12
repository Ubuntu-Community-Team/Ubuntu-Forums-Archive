---
title: "Weird hardware hacks."
date: 2010-10-27
forum: General Help
---

### Post by Silvernail on 2010-10-27
I need a website that can give me information on a weird hardware hack I want to do.

I have tried searching google and the terminology I use does not give me the information I want.

I have a Canon PowerShot A720. It does not work as a webcam. Many years ago I had a Sony that if  you left the memory stick out, it would stream video  
straight through to the USB cable and then to the computer. The Canon will not do that.

I would like to trick the Canon into thinking that a memory card was in place. I want to build a USB cable that has the male memory card connection on one end that I can plug into the camera and a USB connection to my computer on the other.

Anyone have any suggestions, thoughts, insults, flames, rants, rages, fratches or should I quit being cheap and go buy a real video/web cam?

Thanks for any/all the above.
Dave  :confused:

---

### Post by no2498 on 2010-10-27
i think you would get more help asking the ones that make the cards
it does sound as it could work tho

---

### Post by Silvernail on 2010-10-28
Wonder why a null modem cable to connect between the camera and a card reader wouldn't work just as well?

---

### Post by no2498 on 2010-10-28
would be the program for the reader

---

### Post by Silvernail on 2010-10-29
> **no2498 said:**
> would be the program for the reader
Babbling off the top of my head.

The card readers would act like a FIFO file.
And if this code snippet will take video off of a 'tape cassette video camera', 

```
#! /bin/bash
## Rip analog tapes from camcorder to digital
## Sunday May 30, 2010
## Using Dazzle device

# check if there is no command line argument
if [ $# -eq 0 ]
then
echo "You forgot the required image name to be used!"
echo "Usage :: new image name"
exit
fi

mencoder tv:// -tv driver=v4l2:input=0:norm=ntsc:width=720:height=480:outfmt=yuy2:device=/dev/video1:forceaudio:audiorate=48000:adevice=/dev/dsp1 buffersize=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=5000:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -ffourcc divx -o "$1".avi
```
Something could be coded to read the mount point and output it upstream.

---

