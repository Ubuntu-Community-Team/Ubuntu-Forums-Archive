---
title: "Macromedia Fireworks PNG Files"
date: 2006-06-05
forum: General Help
---

### Post by farfromrest on 2006-06-05
Well I have a problem after switching to ubuntu and only one problem, maybe some one can help me. 

On Windows I used Macromedia's Firework program for all my web sites I did. Now by default it saved the "source" file as a PNG, but includes the data for the layers and everything, just like Photoshop's PSD files. 

Well I'm not sure, but I am pretty sure GIMP will open up PSD's and see all the layers and everything works great. Now I for sure cannot do that with a Firework's PNG, not that I know of at least. 

I just need to know if there is anything I can do on my linux machine to read those files with all the layer information. I just don't want to have to reboot windows just to get these files back as how I need them. 

Thank You.

---

### Post by pedalwrench on 2006-08-27
I'd like to bump this.

I too have the same issue.

---

### Post by MarcDM on 2006-08-27
Based on what I could find around the web, it seems that the layers information that Fireworks puts in the files, are known only to Macromedia. That GIMP can read these special *.png files is a feat in itself.

[https://lists.xcf.berkeley.edu/lists/gimp-user/2006-July/008287.html](https://lists.xcf.berkeley.edu/lists/gimp-user/2006-July/008287.html)
[http://www.mail-archive.com/gimp-user@lists.xcf.berkeley.edu/msg07336.html](http://www.mail-archive.com/gimp-user@lists.xcf.berkeley.edu/msg07336.html)

And according to the PNG Spec, they're allowed to do this. 
[http://www.w3.org/TR/PNG/#14EditorsExt](http://www.w3.org/TR/PNG/#14EditorsExt)

So it looks like you're gonna have to use FW in Wine. I've done it, it works ok-ish.

---

