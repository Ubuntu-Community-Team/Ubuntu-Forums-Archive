---
title: "Font selection failure in 2.8 w/Ubuntu"
date: 2012-08-22
forum: General Help
---

### Post by brohan76 on 2012-08-22
Hi there, and thank you for looking at my post. I have many programs on my Ubuntu 12 machine that use text, LibreOffice, Scribus, etc. Each of those works quite well. In GIMP 2.8, the entire program works fine for my from what I can tell with the exception of the text tool. I can select the tool, enter text, I can bold, underline it, I can change to color, as well as the fint size. GIMP will crash however each and every time I try to change the font, be it on the floating text dock (above the text window on the canvas) or the Text toolbar on the left had side of the screen (single window mode). I get no drop down selection box, I merely click in either area, a short freeze of the program and the program quits. Any suggestions, or any error report I can send/paste? I am relatively new to bu reporting in Ubuntu, so would need step by step instructions of necessary documentation etc.

---

### Post by brohan76 on 2012-08-22
I started GIMP from a terminal here is what I received:

(gimp:5544): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Script MT Bold, Bold 16'

(gimp:5544): Pango-WARNING **: font_face status is: out of memory

(gimp:5544): Pango-WARNING **: scaled_font status is: out of memory

(script-fu:5551): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (core dumped)

All I did was start a new document, select text tool, typed text, selected all, then selected the font change button, then it crashed.

---

### Post by irv on 2012-08-22
I took a quick look to see if there were any bug reports on this and I found this bug report that mentions some problems with the text feature. Take a look and see if any part of this bug applies to your problem.
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/994230]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/994230")

---

### Post by irv on 2012-08-22
> **brohan76 said:**
> I started GIMP from a terminal here is what I received:

(gimp:5544): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Script MT Bold, Bold 16'

(gimp:5544): Pango-WARNING **: font_face status is: out of memory

(gimp:5544): Pango-WARNING **: scaled_font status is: out of memory

(script-fu:5551): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (core dumped)

All I did was start a new document, select text tool, typed text, selected all, then selected the font change button, then it crashed.

Looking at your output from running gimp from the terminal it might have something to do with what theme and system font you are using. I tried loading gimp from a terminal and it loads my theme "Black Opal along with it's fonts. 
This one line 
> (gimp:5544): Pango-WARNING **: scaled_font status is: out of memory
is saying you are out of memory. When you are running gimp, open a terminal and run 
```
top
```
it should show how much memory, cpu, and swap you are using. This whole thing might be a memory issues.

From a radical point, you could do a complete uninstall of gimp, change to a different theme and font, re-install gimp and see if the error goes away.

---

### Post by brohan76 on 2012-09-13
Thank you for the responses. I checked out the referenced bug, I don't see anything regarding the text tool issues. I am no that techie, so I very well my have missed what you were trying to point out.  

As for memory, After starting GIMP, I have a lot of memory available. I can make a simple 640x480 100dpi canvas and it closes on changing the text tool. 

What I can do is click on the default Sans font, delete the last s, and 4 options appear in the drop box Bold, etc. I can delete the "n" and the "s" and get more options. I can delete all the way back to the "S" where all of the S fonts, and T fonts show up then it crashes. Perhaps I have too many fonts for Gimp to handle?

I did try uninstalling GIMP, and reinstalling in a different theme, same problem, I installed on the default Ubuntu desktop.

Any other thoughts are appreciated.

---

