---
title: "Slow Programs"
date: 2006-02-01
forum: General Help
---

### Post by lynx2cross on 2006-02-01
I'm new to linux but I love Ubuntu so far.  I'm not a gamer but when I tried to load a program called "Celestial"  it's some type of program so you can view planets and space it seemed really slow.  I used synaptic and downloaded it but when I opened the program up my mouse cursor moved really slow and everything was so sluggish.  I don't if it's my old pc.  It's a Compaq 5000 don't know how old it is, lets just say it came pre-installed with Win.98 2nd edition.  So maybe thats why it's so slow with a program like "Celestial"  Everything else in Ubuntu works great though.  I also tried to play "Penguin Racer"  and the pc once again slowed to a crawl.  I would appreciate any suggestions on what I should do to fix this if it can be fixed.

---

### Post by slavik on 2006-02-01
It's probably the older hardware ... could you list your hardware specs? (CPU, RAM and video card are of most importance).

---

### Post by Protex on 2006-02-01
I'm going to assume it's a graphical issue.

Mind posting your Video Card specs?

---

### Post by lynx2cross on 2006-02-01
How do I find out the specs?  I know I have 256RAM and it's a Pentium lll.  I went to the Ubuntu Hardware Database and here is what it came back with for my pc.  I hope this is the info you need.

	Vendor: GenuineIntel
Speed: 698.025 MHz
Model: Pentium III (Coppermine) 	
		Memory: 256 MB
Swap: 746 MB	
		Videodriver: "i810"
Colordepth: 24
Videomodes: "1024x768" "800x600" "640x480"

---

### Post by akiro.yamamoto on 2006-02-02
Penguin Racer needs a 3D card to operate properly. 
The Intel i810 card is a built-in Video Card with shared resources (CPU and Memory).
This card is designed for BASIC Office and Desktop use NOT Gaming or 3D Acceleration Apps. Sorry.
If you want to use 3D Apps you will need a 3D Video Card. In your case a NVIDIA PCI Card might just do the trick.
Go to :
[http://www.pricewatch.com/](http://www.pricewatch.com/)
Search for : PCI Nvidia Video Card
You'll see some with prices starting @ $23.00
I know that it's only a 32MB TNT2 Card, but anything faster will be wasted on your system anyway. The Motherboard and CPU will become the bottlenecks (as far as 3D performance goes) rather quickly. So a 265MB GeForce card will cost alot more but will not give you the performance boost to offset that cost.

---

### Post by akiro.yamamoto on 2006-02-02
I almost forgot:
The reason I specified a PCI card and not an AGP solution is that as far as I know 
your system only has PCI slots on the Motherboard. I think that was part of the Intel Specification. The Intel i815 (some) have an AGP built onto the Motherboard.
Of course YMMV (I could be wronge ;) ) so be guided accordingly.
Akiro

---

### Post by akiro.yamamoto on 2006-02-02
If You need install instructions don't be afraid to ask anyone here. ;)

---

### Post by lynx2cross on 2006-02-02
Thanks you've been a big help.  I've just learned how to install memory not to long ago so installing a video card should be easy, I hope.  I'll be sure to come ask for help if need be.  I'm going to search the web for instructions and tools I may need to for this.  Wish me Luck!

---

### Post by ximok on 2006-02-03
[QUOTE=lynx2cross]How do I find out the specs?  I know I have 256RAM and it's a Pentium lll.  I went to the Ubuntu Hardware Database and here is what it came back with for my pc.  I hope this is the info you need.

	Vendor: GenuineIntel
Speed: 698.025 MHz
Model: Pentium III (Coppermine) 	
		Memory: 256 MB
Swap: 746 MB	
		Videodriver: "i810"
Colordepth: 24
Videomodes: "1024x768" "800x600" "640x480"[/QUOTE]

Is that by chance a Gateway E3400?

---

### Post by ximok on 2006-02-08
We have a bunch of boxes running off the i810 driver as well.. here is what we found out.  3D support won't work for the i810 driver UNLESS you have the color depth at 16 (not 24 like the default).  Most users won't notice this and will prefer the loss from Millions of colors to 65,000 for the ability to have 3D accell.

So, here is what we did.  We set the default depth at 16, and got rid of all resolutions above 1024x768  (This is all done in /etc/X11/xorg.conf )

You can test your settings by typing ```
 glxinfo | grep render 
```
This will tell you whether or not rendering is supported.  Basically, it'll tell you yes or no.

Oh, also, we set the VideoRam to at least 16 megs. I'll try to post our xorg config tomorrow.

---

### Post by dcstar on 2006-02-08
[QUOTE=lynx2cross]How do I find out the specs?  I know I have 256RAM and it's a Pentium lll.  I went to the Ubuntu Hardware Database and here is what it came back with for my pc.  I hope this is the info you need.

	Vendor: GenuineIntel
Speed: 698.025 MHz
Model: Pentium III (Coppermine) 	
		Memory: 256 MB
Swap: 746 MB	
		Videodriver: "i810"
Colordepth: 24
Videomodes: "1024x768" "800x600" "640x480"[/QUOTE]
Have a read of this (if you aren't already using a 686 kernel):

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

