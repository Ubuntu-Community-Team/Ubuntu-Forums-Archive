---
title: "Screen Recording With Sound"
date: 2011-12-27
forum: General Help
---

### Post by enrico3181 on 2011-12-27
Hello everybody,
my question is: is there any screen recorder with sound?
i already used recordmydesktop but at the result i had no sound.

please help me!

PS: sorry for my bad English, I am from Holland:guitar:

---

### Post by stinkeye on 2011-12-27
I can get sound with recordmydesktop by using pavucontrol.
```
sudo apt-get install pavucontrol
```
Then start up pavucontrol.(start typing pavucontrol in the dash and it will show.)
Goto the recording tab. It will initially be blank.

Now start recording with recordmydesktop (make sure sound is checked).

In the recording tab of pavucontrol you will now see a recordmydesktop entry.
Choose where to capture sound from.
The "monitor" ones will record music as you listen to it.

[**_[COLOR="DarkRed"]Convert OGV to AVI (gtk-recordMyDesktop)[/COLOR]_**]("http://techaccesstips.blogspot.com/2009/04/convert-ogv-to-avi-gtk-recordmydesktop.html")

---

### Post by enrico3181 on 2011-12-27
**Anybody?**

---

### Post by enrico3181 on 2011-12-27
> **himanie said:**
> i can't open a new discution. who can you help me please ! :S so sorry
you have the same problem?

---

### Post by stinkeye on 2011-12-27
> **himanie said:**
> i can't open a new discution. who can you help me please ! :S so sorry

Go back to the General Help section and click on the **New Thread** button at the bottom.

---

### Post by xc3RnbFO8P on 2011-12-27
Here is what I use:
> ffmpeg -f alsa -i pulse -f x11grab -r 30 -s 1920x1200 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.avi
Install ffmpeg
and change the screen size.

ctrl - c, to stop recording.

---

