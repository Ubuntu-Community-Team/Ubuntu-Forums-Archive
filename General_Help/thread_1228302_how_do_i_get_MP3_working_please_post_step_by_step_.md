---
title: "how do i get MP3 working??? please post step by step process"
date: 2009-07-31
forum: General Help
---

### Post by autopilot888 on 2009-07-31
hello i just installed ubuntu and am frustrated that mp3 doesn't work and i have to go through a complicated process to get it to work.

can someone please post the step by step process to get mp3 to work? the help files are too complicated

thanks

---

### Post by credobyte on 2009-07-31
In terminal ( Applications / Accessories / Terminal ):
```
sudo apt-get install ubuntu-restricted-extras

```

---

### Post by ibutho on 2009-07-31
Hi and welcome to the forums. The Ubuntu help docs mention that you can do the following
>     *

      Go to Applications &#8594; Add/Remove Software
    *

      Set Show: to All available applications
    *

      Search for ubuntu-restricted-extras and install it


Have you tried that?

---

### Post by Suff on 2009-07-31
It should auto install the updates if you are connected to the Internet and try to play the mp3, anyways thats how it was with me.

---

### Post by credobyte on 2009-07-31
> **Suff said:**
> It should auto install the updates if you are connected to the Internet and try to play the mp3, anyways thats how it was with me.

Which update includes gstreamer ? :roll:

---

### Post by slakkie on 2009-07-31
Maybe try this script: [http://www.zoef-pc.nl/zooi/multimedia.sh](http://www.zoef-pc.nl/zooi/multimedia.sh)

It adds the medibuntu packages and installs several packages for you. When you have downloaded the script you see what will be done by using `cat multimedia.sh'.

```

wget http://www.zoef-pc.nl/zooi/multimedia.sh
chmod +x multimedia.sh
sudo ./multimedia.sh

```

GL

---

### Post by Suff on 2009-08-01
> **credobyte said:**
> Which update includes gstreamer ? :roll:
If you go to add/remove and type "gstreamer" in the search you can install it most likely.

---

### Post by credobyte on 2009-08-01
> **Suff said:**
> If you go to add/remove and type "gstreamer" in the search you can install it most likely.

I'm not asking, how to install gstreamer. You said that it will most likely be installed after doing an update and I wanted to know, where I could find such an update :p

---

### Post by 3rdalbum on 2009-08-01
> **autopilot888 said:**
> hello i just installed ubuntu and am frustrated that mp3 doesn't work and i have to go through a complicated process to get it to work.

can someone please post the step by step process to get mp3 to work? the help files are too complicated

thanks

Step-by-step process:

1. Connect your computer to an Internet connection
2. Go to System > Administration > Software Sources. Click to enable the top 4 checkboxes, and then click the "Third Party" tab and enable the top 4 checkboxes there too, for good measure.
3. Close the Software Sources program, and when it asks you to reload the package list, click Reload.
4. Open Totem Movie Player, and drag an MP3 file onto it.
5. When it asks you if you want to search for the codec, click OK. It will give you a list of appropriate codecs to install to handle MP3 files. Check them all and click Install.

---

