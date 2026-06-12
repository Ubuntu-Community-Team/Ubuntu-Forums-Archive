---
title: "Photography and such"
date: 2012-01-26
forum: General Help
---

### Post by dat789 on 2012-01-26
I'm into photography and such. Been used to software like Photoshop, Lightroom, and Bridge to manage, organize, and edit photos.

Gimp is probably the closest thing to Photoshop albeit I'd admit I haven't messed much with it. While I'm completely oblivion to the fact of a better alternative, I'd still need to ask if there are any better alternatives to the likes of Adobe Photoshop, Lightroom, and Bridge in the Ubuntu environment?

Thanks for your input.

---

### Post by conradin on 2012-01-26
[http://www.darktable.org](http://www.darktable.org) is supposedly a lightroom esque product. I thought lightroom had a varion out for linux, but I may be mistaken. A friend of mine took some time to learn GIMP, and inkscape, and Ive seen him use it to the same ability and extent that Ive ever seen anyone use photo shop.

---

### Post by muteXe on 2012-01-26
Morning,
I've not used it meself, but there's 'gimp shop', which is supposed to be gimp but have the look and feel of photoshop.  I can understand this as i find the gimp interface not that 'natural'.

[http://gimpshop.com/](http://gimpshop.com/)

---

### Post by dat789 on 2012-01-26
I remember it took me more than 6 months before getting used to the environment in Photoshop. On top of that then came along the CS suites. The learning curve was definitely a challenge but overcame nonetheless.

Perhaps one would and should expect the same for Gimp and/or its variants? It's not mainstream yet because the world of Linux or non-DOS environment has less than a quarter users worldwide (correct me if I'm wrong).

---

### Post by fragos on 2012-01-26
To accomplish all the kinds of things Photoshop does GIMP for me is the best choice. I do use gthumb for my basic viewer and it can accomplish many basic editing needs. If you want to work with the RAW format from digital cameras I'd suggest rawtherapee although if you install ufraw you'll have similar capabilities within GIMP. I only run Ubuntu so I've never used Lightroom but if I'm not mistaken rawtherapee is somewhat anagous from a capability standpoint.

---

### Post by ElSlunko on 2012-01-27
Darktable is great as mentioned. If you're into commercial software like you mentioned check out aftershot pro :

[http://www.corel.com/corel/product/index.jsp?pid=prod4670071](http://www.corel.com/corel/product/index.jsp?pid=prod4670071)

Corel bought up Bibble 5 and changed some things for their first release. Where it goes from here, who knows. I use it myself in my photography business.

---

### Post by fragos on 2012-01-27
Aftershot Pro and rawtherapee are very similar.

---

### Post by rcbfour on 2012-01-27
What you can do is use an online, free tool that I happened upon called pixlr. Pixlr offers a lot of tools, and it's free and online, so you can use it from any computer with internet access. You don't even need an account to start. (however, it isn't as sophisticated at photography, so it may not be as good as gimp.) [http://pixlr.com/editor/](http://pixlr.com/editor/)

---

### Post by dat789 on 2012-01-27
Thanks a lot! These ideas are really good.
I'm afraid it's going to take some time to learn and get used to them moving forward.

---

### Post by dave0109 on 2012-01-27
I've also been using Shotwell as a replacement for the Photoshop Organizer.

---

### Post by I2k4 on 2012-01-29
Right now I'm using GIMP with the UFRaw plug-in and gThumb as a quick-and-dirty viewer editor (though I miss Windows FastStone for that.)  I'm very impressed with RawTherapee 4 (beta), however, and might be changing my workflow for it.

BTW, I recently came across this site by a guy who provides a PPA of interesting photography apps - as a newcomer, it helped me install RawTherapee 4 in the Synaptic Package Manager.

[https://launchpad.net/~dhor/+archive/myway](https://launchpad.net/~dhor/+archive/myway)

For me, it's something of a gold mine of things to try out.

---

### Post by Rodney9 on 2012-01-29
Add the ppa to your software sources, you click on 'Technical Details' to copy the ppa, as I have below.

Then update, then download through Synaptic or Software Center the programs you want from his ppa.

deb [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu) maverick main  

More on how to add ppa's - [http://blog.launchpad.net/ppa/how-to-add-a-ppa-to-ubuntu](http://blog.launchpad.net/ppa/how-to-add-a-ppa-to-ubuntu)

Rodney

---

### Post by Biciclettapc on 2012-04-29
I own Bibble and Photoshop ACR. Bibble is really just a RAW editor and lacks the in depth stuff PS can accomplish

Bibble is fine, but lacks a lot over photoshop of which I am comfortable with.

I shoot a lot of sporting event photography (runners/cyclist/Tri's) and I always go back to PS to deal with my images.  Actually the ONLY reason I still have windows on any of the systems I own.  I shoot only RAW, and 95% of my work is done in PS's ACR with batch processing.  Bibble does deal with batch actions but not as smoothly nor as cleanly as PS.

But, if I were only dealing with a few images and not a 1000 + for each event I could make Bibble or the other RAW open source processors work.

Never used GIMP, but its on my list of things to one day experiment with.  :)

---

### Post by PayPaul on 2012-05-01
I like Darktable for its powerful plugins and effects but it is a butcher of time when it comes to the clunky and tedious method for "exporting" images. I do NOT want to have to type in a file path to save a file. What century is the developer in? Ubuntu and most other OS's have a save as feature allowing you to chose the folder destination and filename of anything you are trying to save.

---

### Post by arunssha on 2012-07-14
> **PayPaul said:**
> I like Darktable for its powerful plugins and effects but it is a butcher of time when it comes to the clunky and tedious method for "exporting" images. I do NOT want to have to type in a file path to save a file. What century is the developer in? Ubuntu and most other OS's have a save as feature allowing you to chose the folder destination and filename of anything you are trying to save.

Well i think  you don't have to type in every time. Use file path variables available inside darktable. For example i have set it to as below:
$(FILE_DIRECTORY)/darktable_exported/$(FILE_NAME)_$(SEQUENCE)

this will always export my pictures to a directory named "darktable_exported" inside current directory with filename same as actual file + a sequence number(just like lightroom).

I hope  I understood your problem correct.


However, I am dealing with many other problems in darktable. 
1. It fails to export a picture after exporting 5-6pictures. Then i need to restart it. Increasing memory reduced this problem but could not resolve it.
2. It crashes many times in a day. So i am supposed to keep moving it to lighttable mode otherwise i'll loose all changes.
3. And now from past few days for some reason it doesn't import a picture at all. I have posted this issue on this forum but haven't got any response.:(

I would still say if you were a lightroom user darktable is pretty good substitute.

---

### Post by EnteRCup on 2012-07-14
I'm pretty sure you could run Photoshop using Wine :)

---

### Post by matt_symes on 2013-02-23
Old thread. Closed

---

