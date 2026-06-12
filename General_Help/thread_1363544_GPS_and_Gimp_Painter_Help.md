---
title: "GPS and Gimp Painter Help"
date: 2009-12-24
forum: General Help
---

### Post by Railgun on 2009-12-24
Let me start off by saying I have absolutely NO experience in Linux whatsoever. I've been a Mac user most of my life, and recently decided to use Ubuntu 9.10 64-bit on my new desktop computer. I'm also an artist, and mainly use Gimp with Gimp Paint Studio and Gimp Painter added. 

I'd like to do this on Ubuntu, but I have no clue how to add GPS and Gimp Painter to Gimp in Ubuntu. I've never used terminal before, and wouldn't have a clue what to do. Can anyone help me out?

---

### Post by alex4c on 2010-03-14
I'm new to Linux too. An I have also installed 9.10 64-bit on my computer. 
I have found this:
[COLOR=Indigo]_***[http://www.webupd8.org/2009/05/gim-paint-studio-gimp-optimized-for.html](http://www.webupd8.org/2009/05/gim-paint-studio-gimp-optimized-for.html)***_
 [/COLOR]an instruction how to install GPS (GIMP Paint Studio).
But...
Let's start from the beginning. I downloaded GPS and as instruction said open: /home/username/.gimp-2.6    ...but wait...there's no file or folder called .gimp-2.6. 
Well ok maybe it is somewhere else so I found something similar in /usr/share/gimp/2.0
There are brushes pallets and patterns (and a few other) folders inside it. I tried to paste GPS brushes into the Brushes folder, but of course I couldn't  because I'm not a root user. So I learned how to change my root password and login as root user. Then I successfully pasted GPS brushes into the Brushes, patterns into the Patterns and pallets into the Pallets folder. When I open up the Gimp I had new brushes patterns and pallets inside. 

The problem started when I realized I don't have tool-options folder and files: sessionrc, toolrc. I searched File System for them but couldn't find them. So my GIMP doesn't have all the GPS features which is very lacking because I got used to them and they are very useful. 
I tried reinstalling GIMP but that didn't help. 
Can somebody help? 
Where GIMP stores presents?
Maybe I overlook something? I am very new to Ubuntu. 


@Railgun   If you have /home/username/.gimp-2.6  I think you won't have much problems just follow the instruction above.

---

### Post by alex4c on 2010-03-15
I've got in now! 
Folder /home/username/.gimp-2.6 is sometimes hidden so go to the view, check show hidden files and there it is. Then just follow this instruction
_***[http://www.webupd8.org/2009/05/gim-paint-studio-gimp-optimized-for.html](http://www.webupd8.org/2009/05/gim-paint-studio-gimp-optimized-for.html)***_
and GPS will be installed. 
I haven't tried installing Gimp Painter.

---

