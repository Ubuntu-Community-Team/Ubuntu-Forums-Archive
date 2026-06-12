---
title: "How to write a shell script to extract files from an SD memory card in the background"
date: 2010-08-20
forum: General Help
---

### Post by shuukazedojo on 2010-08-20
Hello. I'm looking for a way to insert an SD memory card into my computer and have it copy the files from it (a specific directory) in the background while I view the images from the desktop. I heard this may be possible by writing a shell script, but because I have no experience in doing so, I thought I would turn to the forums. 

Thank you for your help!

---

### Post by jsstn on 2010-08-20
try reading this: [http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/). 
the maybe use ```
cp -r a_specific_directory your_dest_dir
``` in your script.
and if you want the script to show you the images too, you could for example do ```
eog a_specific_directory/*
```but why not use f-spot or shotwell or some other image importer?
(also [http://tldp.org/LDP/abs/html/ ]("http://tldp.org/LDP/abs/html/")for all your scripting needs)

---

### Post by shuukazedojo on 2010-08-20
I'll try this out and see how it goes. 

I'm trying to copy this in the background so it's not obvious to other people looking over my shoulder that I'm copying these files. Ya know, secret ninja spy stuff. LOL. 

My alternative is to simply mount the SD card, drag and drop to a premade folder to begin copying, then switch to another desktop to hide the process. I think this may be easier in the long run. BUT, just for kicks, I'm going to try the script. 

THANKS!!!

---

