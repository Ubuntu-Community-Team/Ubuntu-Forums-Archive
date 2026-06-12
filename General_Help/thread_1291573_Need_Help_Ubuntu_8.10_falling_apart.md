---
title: "Need Help Ubuntu 8.10 falling apart"
date: 2009-10-14
forum: General Help
---

### Post by ngrieb on 2009-10-14
I need help with a few problems. My machine seems to be slowly disintegrating, and I don't know what I did. 

First off, my Totem player no longer plays Youtube videos. It will find them, but gives me this error message when I attempt to play them:

AN ERROR OCCURED:
Could not open location; you might not have permission to open the file.

(It was working fine till the last time I tried to use it.)

Also, I attempted to install the OpenOffice 3.1 deb tar files. It complained about what was the 3.0 core, so I removed OO_3.0 with synaptic, but there were still complications, and 3.1 never worked. I then just gave up and tried to go back to 3.0, but now I can not upgrade 2.4 to 3.0 any more. Has anyone installed 3.1 on Intrepid? I have already tried using the PPA's and they don't update anything. Solutions? Perhaps I am not installing the 3.1 debs correctly...can I get a refresher.

Also before I noticed all of this Shiretoko seemed to have eaten Firefox 3.0 after an update? What happened there...could this have caused any of this?

---

### Post by ngrieb on 2009-10-15
Ok, so now I at least see a startup screen when I try and open OO 3.1, but it immediately attempts a recovery of a file, and continues to do so constantly. I continually get this error:

terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

I believe it has to do with the JRE. Anyways, I have reinstalled 2.4 for now =-(

---

### Post by ngrieb on 2009-10-17
Ok, after poking around I solved this problem. I had to delete a previous .openoffice/ directory in my home dir. Hope this helps anyone else with this problem.

But I still have the odd Totem Youtube issue.

---

### Post by sirgogo on 2009-10-17
Hi,

You might have changed permissions on folders from root to the user? I tried this about 3 or 4 years ago, thinking it would make life simpler so I didn't have to "sudo" into things all the time... I was wrong.

However, if everything else seems to be working, I'm not sure. Does Totem, itself, run fine? If not, try running it from the terminal with/without "sudo".

Or maybe the plugin for Firefox wasn't installed correctly. Try removing and adding it using Synaptic.

---

### Post by ngrieb on 2009-10-19
Totem itself works, it plays vids off of the disk just fine. It's just that it suddenly wont play Youtube videos. As far as I know I have not changed folder or file permissions lately. My first thought was attempt to sudo totem, but that didn't work.

---

