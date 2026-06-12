---
title: "installing more packages wihout a net connection"
date: 2005-02-08
forum: General Help
---

### Post by jnoreiko on 2005-02-08
My ISP is AOL, so AFAIK I can't get online with Ubuntu.

How can I install packages without a connection to the internet? For example, I'd like to install [inkscape](http://www.inkscape.org/download.php). What do I need to download and what to I do once I'm booted into Ubuntu?

---

### Post by DirtDawg on 2005-02-08
[QUOTE=jnoreiko]My ISP is AOL, so AFAIK I can't get online with Ubuntu.

How can I install packages without a connection to the internet? For example, I'd like to install [inkscape](http://www.inkscape.org/download.php). What do I need to download and what to I do once I'm booted into Ubuntu?[/QUOTE]

Hey. My Linux box isn't hooked up to the net either, and I've noticed there's not much info for people like us. Mostly under "install help" there's alot of advice about Synaptic and the "apt-get" command. 

Anyway, I just installed Inkscape a couple weeks ago. Here's how I did it:

Go here:     [http://higgs.djpig.de/ubuntu/www/hoary/](http://higgs.djpig.de/ubuntu/www/hoary/)
This is the site with all the manual downloads for Ubuntu specific software. Go to the "graphics" catagory and scroll down until you find the "inkscape(0.40-2)" file and click on that. Down at the bottom of that page, there's some white buttons for downloading the package for whatever specific architecture you have (i have ppc, so I downloaded that one). Copy the file to a disk (or transfer it to your Linux box in some way).

I had the file on a CD Rom so I'll use that example. I inserted the CD Rom, then copied the .deb package onto my hardrive. Trying to install directly from the CD Rom did NOT work for me. After copying, I opened the terminal and entered "sudo" to gain root access. I then moved my cwd to the Directory the package was in (example: 'cd /Home/Packages' ). Finally, I entered the command 'dpkg -i <package name>' (example: ' dpkg -i inkscape.for.ppc.deb '

After entering this command, Ubuntu will throw some jibber-jabber on the screen and 1 of 2 things will happen. 1) it says "Everything's been installed!" or something to that effect. 2)The terminal says something about "missing libraries" or "missing dependancies". I had missing libraries, but this was easy to fix. I wrote the names of the libraries down, then went back to the inkscape download page ( [http://higgs.djpig.de/ubuntu/www/hoary/graphics/inkscape](http://higgs.djpig.de/ubuntu/www/hoary/graphics/inkscape) ). Notice all the files with the red dots next to them. If you're missing any libraries, chances are very high they're one of these. Simply clink the link for the library you're missing, and repeat the process above for that library (or libraries). After you install any missing libraries, try installing inkscape again. You're done!

Note: 90% of the time, the programs install under the /usr/bin directory (sometimes '/usr/games' if you install a game). So to run inkscape, look in that directory for a file probably called something like "inkscape4.3", then use the "run" program (I think in Applications menu) and enter '/usr/bin/inkscape4.3'. 
 
It may sound confusing, but I promise it's easy. Of the programs I've installed, almost all have installed without a hitch, and only a couple have required me to install one or two missing libraries. 

Also: If anyone knows an easier way to go about this process, please let me/us know. Supposedly, Synaptic allows installation from the harddrive, but I've yet to find a simple "search" method that would allow me to browse my harddrive for packages. 

Hope this helps! :D

---

### Post by landotter on 2005-02-08
[QUOTE=jnoreiko]My ISP is AOL, so AFAIK I can't get online with Ubuntu.

How can I install packages without a connection to the internet? For example, I'd like to install [inkscape](http://www.inkscape.org/download.php). What do I need to download and what to I do once I'm booted into Ubuntu?[/QUOTE]

You can always install stuff at the commandline:

& sudo dpkg -i packagename.deb

Inkscape has a few dependencies so you might have to search those down as well after parsing the readout when you try to install it like above. 

Good luck!

---

### Post by jnoreiko on 2005-03-28
[QUOTE=landotter]Inkscape has a few dependencies so you might have to search those down as well after parsing the readout when you try to install it like above.[/QUOTE]

I gave up... too many dependencies. I was going from one machine to another, getting packages I needed, and then I broke gnome installing newer versions of things inkscape wanted such as gtk...

---

### Post by DirtDawg on 2005-03-28
[QUOTE=jnoreiko]I gave up... too many dependencies. I was going from one machine to another, getting packages I needed, and then I broke gnome installing newer versions of things inkscape wanted such as gtk...[/QUOTE]

Thats a drag. Strange thing, my inkscape installed fine. I did have to install a few dependancies. Are you using warty?

Also, I just got a 256 Meg flash drive for $20. It makes hopping from one computer to another a _much_ easier process.

Good luck.

---

