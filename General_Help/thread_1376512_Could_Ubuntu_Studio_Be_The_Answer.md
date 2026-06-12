---
title: "Could Ubuntu Studio Be The Answer?"
date: 2010-01-09
forum: General Help
---

### Post by derekeverett on 2010-01-09
Ok - I'll try to make a long story short and then pose my question.

I am not able to get my mic/mixer recording using Ubuntu. This set-up works fine with Windows (dual booting on the same machine) so I know the problem lies with Ubuntu.

I have posted (in great detail) my problems many times now in this forum and I still have no answer. I can hear the output of the mixer through headphones connected to the computer speakers.. but I can't record. Ubuntu can't seem to find the signal.. even though it can "hear" it. 

I have received some advice.. I think installing JACK Control might have been the closest to a solution I got but even JACK won't start and I can't get an answer as to why.

I enjoy Ubuntu. I've been using it for various things for 3 years now. But the problems that do exist are really starting to turn me off. I don't mean to gripe too much but I do understand why some people fall off the deep end in these forums and announce a switch back to another OS. The truth is, every time I actually try to do "work" with Ubuntu I end up throwing my hands up in the air out of frustration and doing the project on Windows or the Mac where I can make things work properly. Being a fool, after some cool off time I come back and try Ubuntu for another project.

If I can't get this mic.mixer input recording audio soon I think this will be the straw that broke the camels back. I've got hours invested in trying to make this work already. It took me less than 10 mins to get this configuration working in Windows and the mac - combined.

But before I do something hasty, I have one question - and I am real curious for some informed opinion here....

Is there any reason that Ubuntu Studio might be the answer for me? If I go through the headache of setting up this machine to dual boot with Ubuntu Studio is there reason to believe my mixer input will just work like it should?

If anybody has a decent theory of why this could work... I'd love to hear it and maybe I will try it! 

Thanks all! This forum has been good to me in the past, and I don't mean to whine... but enough is enough sometimes...

---

### Post by amsterdamharu on 2010-01-09
I thnk the problem lies in alsa, and since ubuntu (I guess ubuntu studio) uses alsa it probably would not fix your problem. I have had several computers where the sound did not work properly and this seems to be a serious linux issue.

As you know there are many different tips on how to fix it but on some computers that I've tried it is just a waist of time.

Currently have sound and rocording working on my ubuntu 8.04.  Doing the following:

    * First you must find which model of sound card you use, so run this command: 

cat /proc/asound/card0/codec#* | grep Codec

It will return model of your sound card(s), for example: "Codec: Realtek ALC260", so your sound card is ALC260.

    * You should open a file in ALSA documentation. This file is here: 

/usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz

    * or if that file does not exist, try: 

/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz

(If you compiled your own kernel or ALSA modules, the documentation for your version can probably be found in the source package you used)

    * Search for your model, and take a look at its types, for example I found the following lines for ALC260: 

hp              HP machines
hp-3013         HP machines (3013-variant)
fujitsu         Fujitsu S7020
acer            Acer TravelMate
basic           fixed pin assignment (old default model)
auto            auto-config reading BIOS (default)

Read all of them and try to find the one which is more similar to your sound card, for example if you have a laptop, you can choose "acer".

    * Open /etc/modprobe.d/alsa-base with the following command: 

sudo nano /etc/modprobe.d/alsa-base

    * In Ubunty Jaunty and more recent, the file ends with .conf : 

sudo nano /etc/modprobe.d/alsa-base.conf

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=MODEL

Double click on the speaker (volume control) edit -> preferences -> tick the capture box and close the window
in volume control you have a tab called recording go there and make sure nothing has a red cross in it.


As far as I know if it doesn't work in Ubuntu now I don't see a reason why it would work with Ubuntu Studio

Hardware support in Linux is not as good as it is in Windows (sound, webcam, video ...) but it has made great progress over the last years and Ubuntu has been a great experience for me so far[B].
[/B]

---

