---
title: "How do I stop Tearing In Video? Intel G41"
date: 2010-05-01
forum: General Help
---

### Post by nexoncore on 2010-05-01
I have Embedded Intel G41 Graphics on my computer, but have noticed that  under window I have no tearing in video, but in ubuntu I do. The ubuntu  version I am using is the new 10.04 LTS.

I recently had to stop desktop effects due to a change in resolution  larger than allowed in metacity. In compiz I have it set to Sync to  Vblank but during video playback there is alot of tearing.

Can anyone help?

---

### Post by nexoncore on 2010-05-01
Can someone please help

---

### Post by nexoncore on 2010-05-01
Anyone?

---

### Post by clhsharky on 2010-05-01
HI nexoncore

I use metacity as my compositor,it at least works right. Compiz is to buggy right now if it works good, if not maybe next update, thats how i look at it right now.
I use xv for video out put, I set it in mplayer and it sets it globally. 
At full screen video gets Sync properly and no tearing.

Sharky

When compiz work right its smooth, so when the stars line up its haven.

---

### Post by nexoncore on 2010-05-01
Problem is graphic issues with metacity, with me having intel G41 graphics, setting it to the high resolution of my monitor causes serious issues. Windows borders fail making it so windows cant be used. To fix this I need to turn metacity to no effects. Now I cant re enable effects hence why compiz is handling the compositor.

---

### Post by nexoncore on 2010-05-02
Anyone?

---

### Post by nexoncore on 2010-05-02
anyone?

---

### Post by Jose Catre-Vandis on 2010-05-02
I am in Xubuntu 10.04, and my setup, using mplayer for all video types resolves any video tearing (ION chipset).

For vdpau (HD/x264) I use gl with no compositing turned on, this sorts out tearing. Less demanding video types can run without tearing on xv (not using vdpau)

See my mplayer config [here]("http://bimma.me.uk/2010/02/14/video-tearing-fixed-xubuntu-910-nvidia-ion/")

Might give you some ideas

---

### Post by nexoncore on 2010-05-03
Thanks, I tried installing mplayer and its confirmed installed but I have no access to it what so ever

---

### Post by Jose Catre-Vandis on 2010-05-03
open terminal and type mplayer

What happens?

---

### Post by nexoncore on 2010-05-03
Basically a few errors but I managed to reinstall using a deb, I am assuming the repository one has an issue or missing the GUI. Regardless disabling the metacity composition did the trick but now I cant use docky, so I am going to have to find a dock which doesnt require composition.

Thanks

---

