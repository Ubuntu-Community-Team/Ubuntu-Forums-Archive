---
title: "64 Bit, powerful system, yet unpowerful?"
date: 2009-09-29
forum: General Help
---

### Post by bd41 on 2009-09-29
For some reason, i lag really hard in this OS.

Ubuntu 9.04 i have 4 gigs of ram, quad process, etc

However in ubuntu im experienceing alot of slowness compared to windows 7.

For example, when i try to play an HD movie which is a large file, the movie barely plays, not watchable, slows my whole pc down, etc.

Im using the 64 bit of ubuntu, should i have used the 32 bit?

---

### Post by misfitpierce on 2009-09-29
No but do you have the correct and newest video drivers installed for your graphics card whether it be ATI, NVidia, or Intel integrated etc etc...

---

### Post by bd41 on 2009-09-29
> **misfitpierce said:**
> No but do you have the correct and newest video drivers installed for your graphics card whether it be ATI, NVidia, or Intel integrated etc etc...

I have the ATI/AMD propriety driver 

my video card is Asus 4870 1G graphics card, are there any other drivers i dont know about?

---

### Post by FunkyRes on 2009-09-29
What are you using to play the movie?
What does top say is using your cpu?
How are the hd movies encoded?

I have single AMD X2 w/ 2GB of RAM and HD movies (h.264 encoded 720p) play for me just fine. Ubuntu Jaunty x86_64, nvidia video, desktop effects turned off.

I'm using totem w/ fluendo decoder pac, but open source decoders should also work fine.

---

### Post by QIII on 2009-09-29
No, you should not have used 32 bit.  You would have sacrificed the benefits of a 64 bit system on 64 bit hardware architecture and taken a hit on the 4GB of memory you have.  The "limit" for a 32 bit system is generally given as 4GB, but it is actually slightly less.  Less still if some of the memory is reserved by things like your video card.

Your experience with speed is unusual.  You might get the impression that there is an issue with speed when you can search for posts here that talk about it.  But keep in mind that nobody comes here to complain about things that are working right.

Which player are you trying to use?

Do you have Compiz running?

Do you have desktop sharing enabled?

Would you get the computer to a point where it is running slowly, open the terminal and post the results of 

```
top
```

so we can take a look at what is bogging you down?

---

### Post by JigglyWiggly_ on 2009-09-29
In a terminal can you write compiz? Because depending on the report you might not even be using your graphics card...(real performance)

But depending on your output do this:

Go to ati's site download the 64 bit linux drivers
Then go into a terminal and do sudo /etc/init.d/gdm stop
then press clrl + alt + f1
relogin then cd to where you downloaded the ati drivers and do ```
 "chmod +x ati-driver filename.run" 
```
Then do sudo -i and cd there again and do
/ati-driverorwhateverthenameis.run

But only do this if me or someone else sees your compiz output. A lot of Linux users are stuck up saying, ati drivers suck they are closed source don't use them... well I kind of agree, but sometimes you just have to use them.

---

### Post by bd41 on 2009-09-30
> **JigglyWiggly_ said:**
> In a terminal can you write compiz? Because depending on the report you might not even be using your graphics card...(real performance)

But depending on your output do this:

Go to ati's site download the 64 bit linux drivers
Then go into a terminal and do sudo /etc/init.d/gdm stop
then press clrl + alt + f1
relogin then cd to where you downloaded the ati drivers and do ```
 "chmod +x ati-driver filename.run" 
```
Then do sudo -i and cd there again and do
/ati-driverorwhateverthenameis.run

But only do this if me or someone else sees your compiz output. A lot of Linux users are stuck up saying, ati drivers suck they are closed source don't use them... well I kind of agree, but sometimes you just have to use them.



Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1920x1080) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

---

### Post by Yellow Pasque on 2009-09-30
> For example, when i try to play an HD movie which is a large file, the movie barely plays, not watchable, slows my whole pc down, etc.

ATI drivers don't offload any HD decoding to the GPU: [http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA)

---

