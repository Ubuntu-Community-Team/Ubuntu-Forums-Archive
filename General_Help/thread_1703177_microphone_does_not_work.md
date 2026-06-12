---
title: "microphone does not work"
date: 2011-03-08
forum: General Help
---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-08
i have problems with my microfone, the microfone is built-in my webcam its microsoft lifecam vx-1000. the webcam works fine, but why not the microphone?? i have chosed the webcam as the default microphone, and its not muted or anything...
the webcam shows up at the input, and its not muted or anything, and when i try to talk in the mic its not showing no movement

---

### Post by 741Baus on 2011-03-20
I received this web cam as a birthday gift yesterday and the mic was not working  so after a bit of research I found this guide from member kyleabaker > My patch has been worked into the maintainers code, and his code is updated regularly, so just download his and try it (currently GSPCA 2.10.2) from:
[EMAIL="http://moinejf.free.fr/"]http://moinejf.free.fr/[/EMAIL]

Then run the usual...
make
sudo make install
reboot 

download the latest code from the above link to desktop extract there open terminal cd Desktop cd (extracted file you have on your Desktop) then run the above commands make . sudo make install . sudo reboot .
I've  tested this with Cheese and I'm getting sound in the video , I also did a sound check with Skype and it worked as a test as of this morning 21/3/2011 I have yet to make a Skype video call , so hope this helps P.

[http://moinejf.free.fr/]("http://moinejf.free.fr/")

---

### Post by gyyug78fg87ogguiioioioioi on 2011-04-16
works great now thanks for the help !:D

---

