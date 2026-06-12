---
title: "trouble watching films"
date: 2009-09-17
forum: General Help
---

### Post by presterjohn on 2009-09-17
I am very new to Linux and thought that Computer Active's special guide book with free Ubuntu disc would possibly be my best intro into this OS. So far I have managed to muddle my way through installing Ubuntu onto the families ancient Compaq presario 700 laptop (built circa 2002)in the end the only way it would work is if I let Ubuntu strip the computer of all its contents and start from fresh. The end result is a slow but serviceable computer that I hope to use as a learning tool for myself (I am thick but keen) and as a basic spare web browser and viewer of Xvid/Divx films and comics.

However this is where I am having problems. I can't seem to get the DVD player working properly even with box standard region 2 films let alone anything that would need a decent set of codecs. and I can't work out how to transfer my download of the Linux comic reader comix on to my lap top. Ubuntu does not seem to have a built in zip type extractor so I am in a kind of catch 22 situation with installing most downloaded programmes really. I should hasten to add that as this laptop in as yet not conected to the internet I am currently downloading from my Windows PC and then transferring files via a memory stick.

---

### Post by marcopolo1981 on 2009-09-17
what version of Ubuntu are you running? 9.04 32bit or 64bit?

Is there any way you can hook up the pc to the internet temporarily while we help you set it up to play DVD's?

---

### Post by NoaHall on 2009-09-17
It does have a built in extractor. Right click, and choose extract here.

Connect it to the internet and do -

Applications -> Accessories -> Terminal

Then type without quotations -

"sudo apt-get install vlc ubuntu-restricted-extras"

---

### Post by presterjohn on 2009-09-17
> **marcopolo1981 said:**
> what version of Ubuntu are you running? 9.04 32bit or 64bit?

Is there any way you can hook up the pc to the internet temporarily while we help you set it up to play DVD's?

That is the version. I assume that it is 32bit though I do not know for sure.

At the moment I am unable to connect the old pc to the internet. I can't find my modems driver disc and it has no pre existing modem drivers. Please remember I am very grateful for any and all replies but I do have to be spoon fed a bit as I struggle with windows XP so Linux is super tough for me to work out.

---

### Post by marcopolo1981 on 2009-09-17
On the pc connected to web, go to [http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html) and download the file called i386 at the bottom of the page.

Go to [http://packages.medibuntu.org/jaunty/w32codecs.html](http://packages.medibuntu.org/jaunty/w32codecs.html) and downloaded the i386 file at the bottom.

Transfer these files to your ubuntu box and double click them one at a time.

If this doesn't work, try rebooting the pc.

If this still hasn't worked after a reboot, post back.


Mark

---

### Post by presterjohn on 2009-09-17
Thanks I will give that a try in the morning.

---

### Post by marcopolo1981 on 2009-09-18
I can't help with the networking problem, but I'm 99% certain that if you found the modems driver disc, that it would be of little use. 
Those drivers are usually for Windows only. Only by using a peice of software called NDISWRAPPER would they come in useful.

Try posting in [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) and somebody there will try to help you.They may be able to help you set up your internet connection without the driver disc.

---

