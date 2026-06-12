---
title: "how to correctly install a tar.bz2 source file???"
date: 2010-04-18
forum: General Help
---

### Post by chris.jericho on 2010-04-18
Hey there Linux brothers,

Since the time I have moved to Ubuntu.... I am finding it difficult to do work on images.... since in Windows I was using Photoshop.. 

But I tried running photoshop using wine and stuff but either didn't work or caused a lot of problems....
So I found a new solution GIMP that is very close to Photoshop but not exactly like that... Now I got another solution that is some modification to GIMP called GIMP shop.

I downloaded the Linux version and I got a file gimp-2.2.8.tar.bz2

I was always confused in how I can install these source... there is no help on their website..
Please somebody help me in installing these source files.... since I need to do many images manipulation and editing for my work. 

Please help me!!!

---

### Post by mick222 on 2010-04-18
Looks like their is a deb package for gimpshop easier to install that tan compiling it yourself.

---

### Post by chris.jericho on 2010-04-18
where can I get the deb package for it???

---

### Post by infinitejones on 2010-04-18
I had a look on the [download page]("http://www.gimpshop.com/download.shtml") for Gimpshop - scroll down a bit and you'll see two useful links:

[This link]("http://linux.suramya.com/tutorials/Install_GIMPShop/") which takes you to a page that looks like a very comprehensive guide on how to install Gimpshop from its source (which is what you've downloaded).

I assume you could just copy and paste the line of codes one at a time into the terminal, hit enter, wait until it finishes and repeat until you're done. (Although I haven't tried it and the page is dated 2005 so there's a chance some of it might not work).

Or, it gives details above each command line about what that does, which is brilliant, because if you read carefully and think about what's happening you'll get a good idea of the general things going on when you install stuff from source.

OR... the next line on the download page is where you can "Get the GIMPshop 2.2.11 for Debian package", which will download a .deb file. Then you can double click on it and it should just install automatically (similar to a .exe in Windows). Again, I haven't tried it myself so I don't know if it does work.

(I should point out, because it's not immediately obvious, that Ubuntu is based on another Linux implementation called Debian, so on the whole, packages for Debian (.deb packages) will work on Ubuntu.)

So the second way's easier, but the first way's probably much more educational!

---

### Post by chris.jericho on 2010-04-18
the debian package that is available is not for 64bit OSs :(

---

### Post by mick222 on 2010-04-18
Looked at the page again seems like this project is dead will probably give you an old version better to just learn to use gimp.

---

