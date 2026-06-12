---
title: "Headphones won't mute laptop speakers - 12.04"
date: 2012-05-14
forum: General Help
---

### Post by buddhuu on 2012-05-14
Hi all,

Running 12.04 and loving it. Only issue to date is that since this install my laptop speakers will not mute when I plug in a headphone jack.

Laptop is Acer Aspire 5920. Sound is identified as Realtek ALC1200.

I tried ALSA Mixer, but that can't get the phones working without the speakers either.

I'd be grateful for assistance - the simpler the better, as I'm pretty simple...

Thanks.

---

### Post by buddhuu on 2012-05-16
No ideas?

---

### Post by forestG on 2012-05-16
i have the exact same problem! 

There are some solutions suggested here:

[http://askubuntu.com/questions/128099/restore-speakers-headphones-option-in-ubuntu-12-04](http://askubuntu.com/questions/128099/restore-speakers-headphones-option-in-ubuntu-12-04)

I have not tried them all, only the first one but it did not work.

Edit: just found this: it is a bug.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/994953](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/994953)

---

### Post by na5h on 2012-05-16
Alsamixer didn't work? What exactly did you do with alsamixer? Did you try to simply decrease the volume of the "speaker" channel using the arrow keys (in alsamixer)?

---

### Post by buddhuu on 2012-05-17
> **forestG said:**
> [...]

just found this: it is a bug.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/994953](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/994953)

Ah yeah, that's the one. Thanks, forestG. 

Guess I have to wait for a fix.

---

### Post by forestG on 2012-05-31
> **na5h said:**
> Alsamixer didn't work? What exactly did you do with alsamixer? Did you try to simply decrease the volume of the "speaker" channel using the arrow keys (in alsamixer)?

In my case the problem is that alsamixer does not recognize the existence of the headphones. It considers the two outputs to be one. So headphones appear to be non-existent (volume to 0 without being able to change it) and the speakers control controls both speakers and headphones

---

### Post by ohdung on 2012-06-02
> **forestG said:**
> In my case the problem is that alsamixer does not recognize the existence of the headphones. It considers the two outputs to be one. So headphones appear to be non-existent (volume to 0 without being able to change it) and the speakers control controls both speakers and headphones

I'm having the same problem, so I guess I'm waiting for a fix too

---

### Post by CrocoDuck on 2012-06-02
Hi. I had the same problem with ubuntu 11.10 on a friend's laptop. Unfortunately I don't remember how we fixed it :( ...

We can start viewing the output of this:

```
aplay -l
```

and this:

```
cat /proc/asound/modules
```

---

### Post by xam72 on 2012-06-10
ho risolto il problema così:

```
$ sudo gedit /etc/modprobe.d/alsa-base.conf
```

e aggiungere la seguente opzione

```
options snd-hda-intel model=auto
```

ciao

---

### Post by ON-F on 2012-06-26
Hi, I had the same problem after upgrading to 12.04.
In my case I solved installing the Realtek codecs from this site:

[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

as suggested in this website (in Italian, with instructions): 

[http://www.supernerd.it/2012/05/29/ubuntu-12-04-risolvere-i-problemi-audio-dovuti-alle-schede-realtek/](http://www.supernerd.it/2012/05/29/ubuntu-12-04-risolvere-i-problemi-audio-dovuti-alle-schede-realtek/)

Hope this helps :)

---

### Post by IWantFroyo on 2012-06-26
I fixed this problem by moving to Gnome-shell.

```
sudo apt-get install gnome-shell
```

I'm still not sure exactly why it worked, though.

---

### Post by fresnofred on 2012-06-30
i had the same prob with a lenovo g555 laptop.  i downloaded ultimate edition 3.0 and tried the live dvd and the speaker muted when i put in headphones.  this is actually a mint os.  try going to ultimate edition's website and downloading and burning a dvd iso image and then boot and see if this takes care of the prob.

---

### Post by beansdad on 2012-07-07
Many, many thanks to xam72. This worked on my Acer Aspire 7730 perfectly!

---

### Post by ON-F on 2012-11-20
I noticed that if I plug-in my headphones before starting Ubuntu,
I  have **only** sound in headphones and nothing from speakers,
*but* if I insert the headphones when the system is active I have 
sound **both** from speakers and headphones.
Anyone in the same situation (acer 5920)?:confused:

---

### Post by ckunzler on 2013-01-29
> **xam72 said:**
> ho risolto il problema così:

```
$ sudo gedit /etc/modprobe.d/alsa-base.conf
```

e aggiungere la seguente opzione

```
options snd-hda-intel model=auto
```

ciao

xam72's solution worked for me. Thanks.

---

