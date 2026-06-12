---
title: "Burning videos to play on dvd player"
date: 2009-07-24
forum: General Help
---

### Post by Benbow on 2009-07-24
I have a number of family videos from my videocam which I want to play on my dvd player for tv viewing. I have edited these on kino but usually when I burn them to dvd it comes out as an iso.

My questions are what format should I be using to play on my dvd and which programme is the easiest to use to get this result?

Thanks.

---

### Post by rogueleader12345 on 2009-07-24
Try Brasero. Select the Video Project on the right. Then add your files and burn, and you should be good to go!

---

### Post by wojox on 2009-07-24
+1 Brasero

---

### Post by Benbow on 2009-07-24
Thanks for your reply. I have tried that but I get an error message saying that Brassero doesn't have the correct plugins?

---

### Post by wojox on 2009-07-24
It doesen't auto search for them?

---

### Post by Benbow on 2009-07-24
No. I wondered why it didn't also!

---

### Post by jasonsjunk on 2009-07-24
I use K3B for all of my burning needs.  It is one of the best burning programs I have ever used.  

And yes I know K3B is a KDE app but it works just fine under Gnome.

---

### Post by wojox on 2009-07-24
On the top taskbar click on

System - Administration - Synaptic Package Manager

it asks for your normal user password, not your SuperUser/Root one. Use the "search" button because it searches in descriptions as well as titles so try searching for "brasero plugins" or something. If already installed they have a green blob beside them but otherwise just right-click and select install. It's also be worth clicking on "Mark all updates" before "Apply".

---

### Post by Bigtime_Scrub on 2009-07-24
If you are going to want to play back your dvd's on a standard dvd player then you need an authorship program. 

```
sudo apt-get install devede
```

You will want to stick whatever video format you have into this program and it will spit out an ISO file that you can burn directly onto a DVD with. YOu can use Brasero, k3b, Gnomebaker or any other burning software.

DeVeDe also lets you add menu's and other stuff too. It takes a good hour to encode an entire DVD but you won't have to worry about plugins. When you install DeVeDe the codecs and plugins you need will be installed as dependencies.

---

### Post by Cheesemill on 2009-07-24
+1 for [DeVeDe]("apt:devede")

---

### Post by vinutux on 2009-07-24
another vote for DeVeDe

---

### Post by Benbow on 2009-07-24
Thanks, Guys for your help. The main item is an 8mm film of a friends wedding which I have now successfully transferred to DVD. They have never seen this and it was taken thirty years ago!! They will be very pleased with the result.

Thanks again.

---

