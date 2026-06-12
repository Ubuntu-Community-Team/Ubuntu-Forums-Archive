---
title: "convert cda (audio cd) into mp3 - what software to use how i can do it ?"
date: 2009-08-14
forum: General Help
---

### Post by ryansdistrict on 2009-08-14
helllo i want 2 convert some music cds i have into mp3s to play on my pc 
how can i convert a  cda (audio cd) into mp3 - what software to use how i can do it ?

---

### Post by Chronon on 2009-08-14
Might I suggest Ogg Vorbis instead?  Anyway, whichever format you use, you can find some information on relevant apps here: [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

I think Kaudiocreator is being replaced by Audex, though.

---

### Post by MrWES on 2009-08-14
> **ryansdistrict said:**
> helllo i want 2 convert some music cds i have into mp3s to play on my pc 
how can i convert a  cda (audio cd) into mp3 - what software to use how i can do it ?

FWIW, Once you try ABCDE (A Better CD Extrator) you'll love it. It's command line, but very robust.

It's available in the repositories, and here is an excellent web site maintained by Andrew.46

[http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

Bill

---

### Post by ryansdistrict on 2009-08-14
i went to abcde 
marked it to synaptic for isntallation and clicked apply 
i dont know if its installed but dont think so 
how to install it cuz nothing is happening when clicking apply

---

### Post by oldos2er on 2009-08-14
> **ryansdistrict said:**
> i went to abcde 
marked it to synaptic for isntallation and clicked apply 
i dont know if its installed but dont think so 
how to install it cuz nothing is happening when clicking apply

 As was mentioned, abcde is a CLI app; start it by opening a terminal and typing abcde.

 If you prefer a GUI app, there is Sound Converter, among others.

---

### Post by MrWES on 2009-08-14
> **ryansdistrict said:**
> i went to abcde 
marked it to synaptic for isntallation and clicked apply 
i dont know if its installed but dont think so 
how to install it cuz nothing is happening when clicking apply

Open a terminal; Applications | Accessories | Terminal and then type abcde to check if it's installed. If not, maybe you need to enable the multiverse and universe software sources.

Also, check the web site I posted, there is a good example of a .abcde.conf file you need for ripping to MP3.

Bill

To edit the .abcde.conf

Hit ALT + F2 and type gedit .abcde.conf, edit the file to match the example shown at the web site I posted for MP3.

---

### Post by Chemical Imbalance on 2009-08-14
I recommend you use sound-juicer.  It's a GUI app and easy to use.

It shows up as Audio CD Extractor in the menu after installation.

---

### Post by scouser73 on 2009-08-15
Use **Audio CD Extractor**, which can be found in **Add/Remove**, you can then rip CD's to MP3 format.

---

### Post by Chemical Imbalance on 2009-08-15
> **scouser73 said:**
> Use **Audio CD Extractor**, which can be found in **Add/Remove**, you can then rip CD's to MP3 format.

See the post above you :)

---

### Post by R_W322 on 2009-08-15
Rhythmbox has worked just fine for me just click copy-cd.

(i have the gstreamer pluggins installed though)

RYAN.WDZIECZNY

---

