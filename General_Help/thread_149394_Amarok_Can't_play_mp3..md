---
title: "Amarok Can't play mp3."
date: 2006-03-23
forum: General Help
---

### Post by wcks48 on 2006-03-23
As taught by the amarok website FAQ i installed and update the amarok-xine, then switch the engine of amarok to xine too. this time, the mp3 files could be load into the amarok playlist but after click it to play the mp3, very fast, the whole mp3 finished running. so no sound could be heard from. any problem here?

---

### Post by Swiss on 2006-03-23
Yes, Ubuntu does not come with MP3 codecs, therefore you cannot play MP3 files until you get the Codec.

---

### Post by wcks48 on 2006-03-23
then how could i do to fix the codec for mp3?

---

### Post by bailout on 2006-03-23
I am on dapper now so I am not sure it is the same on breezy but search for libxine-extracodecs or similar in adept. If you find it install and you should be good to go.

---

### Post by Terracotta on 2006-03-24
[QUOTE=bailout]I am on dapper now so I am not sure it is the same on breezy but search for libxine-extracodecs or similar in adept. If you find it install and you should be good to go.[/QUOTE]

I am on dapper too (64-bit), but I can't find libxine-extracodecs or similar in the repos?

---

### Post by Jucato on 2006-03-24
Here are the instructions from the Ubuntu wiki (scroll down to the MP3 and restricted codecs section): [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
And here's one from the Kubuntu wiki: [http://www.kubuntu.org/faq.php#mp3s](http://www.kubuntu.org/faq.php#mp3s)

For you ducks out there (Dapper users), the Ubuntu wiki on Restricted Formats have been updated to include instructions for Dapper as well. :D

---

### Post by 604 on 2006-03-24
I installed gstreamer plugin, w32 codecs, did the stuff with repositories, but still no sound with mp3s. (im using dapper)

---

### Post by Barrakketh on 2006-03-24
[QUOTE=604]I installed gstreamer plugin, w32 codecs, did the stuff with repositories, but still no sound with mp3s. (im using dapper)[/QUOTE]
Dapper's amaroK doesn't have the Gstreamer engine installed.  libxine-extracodecs is in Dapper's multiverse repository.

---

### Post by Neo Ex on 2006-03-24
After having installed gstreamer0.8-plugins, have you run 'gst-register-0.8' from a terminal?

---

### Post by wcks48 on 2006-03-25
I even don't have the gstreamer0.8-mad  dun know why, after i download it and tried to install the package, the system stop and shows that many files not there as required, eg: libglib2.0.0 , libid3tag0 , libmad0 , libxm12. so my gstreamer0.8-mad installed with broken. i dun know how to retrieve the said files from Adept. pls help... i lost playing all types of multimedia file in kubuntu, like mp3, .mov, .rmvb, etc.

---

### Post by Barrakketh on 2006-03-25
[QUOTE=wcks48]I even don't have the gstreamer0.8-mad  dun know why, after i download it and tried to install the package, the system stop and shows that many files not there as required, eg: libglib2.0.0 , libid3tag0 , libmad0 , libxm12. so my gstreamer0.8-mad installed with broken. i dun know how to retrieve the said files from Adept. pls help... i lost playing all types of multimedia file in kubuntu, like mp3, .mov, .rmvb, etc.[/QUOTE]
Wait...you said "after I download it" I'm not sure if you're doing it right.  I'm skipping adept here, but do the following:

Open Konsole.

Type in "sudo apt-get install gstreamer0.8-plugins".  You need to have the Universe repository enabled.

---

