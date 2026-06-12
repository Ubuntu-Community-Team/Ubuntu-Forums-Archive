---
title: "XSANE strange behavior and resizing of output"
date: 2011-02-18
forum: General Help
---

### Post by Bladeforger on 2011-02-18
I have used XSANE for scanning for several years, and it has recently been giving me trouble.  It resizes when I copy, and it resizes when I scan into a multipage pdf.  It's not drastic, an 8.5 x 11 page gets shrunk down to about 7.5 x 10.  

I've installed the Gnome scanning utility to get by, but the resolution just isn't as great.  

I went into Synaptic and marked all the XSane packages for reinstallation and reinstalled them.  However, my contrast / gamma settings remained the same, and, as you might guess, whatever is shrinking my output remained the same also.  I don't know how I could have changed a setting accidentally, but it looks like I must have done so... or something else did it for me.

Any help is appreciated,
Keith

---

### Post by Bladeforger on 2011-02-21
As a follow-up, after some reading, I did manage to reset some of the options.  I also discovered that if you go into Nautilus via terminal using > sudo nautilus then you can click to view hidden files and navigate to /home/username/.sane/xsane and rename the xsane.rc file to something else (MessedUp_xsane.rc).  Then when you execute xsane it makes a new one.

I'm still getting a resizing.  Playing around with copy (as opposed to multipage) I set the printer up under preferences and gave it 21.5 x 27.9 cm as the printer dimensions.  Playing with the gamma doesn't change the size.   My output is "shrinking" to 7 3/4 inches, i.e. 19.6 cm wide.  I'm getting almost 1/2 inch of the page CUT OFF from the right side, and the remainder is just resizing of the image.  That's with a left offset of 0 cm.

When I set the left offset to .5 cm, which is about the 1/2 inch I'm missing, then it just gets worse... 

So I set the offset to -0.500 cm.  INTERESTING.  Now, the left side comes out with the half-inch mark right at 1/2 inch from the left.  I, of course, lose the 3/16 that the printer just won't print.  Naturally.  On the right side, my 1/2 inch mark is 3/4 inch from the edge... guess I could live with that, but I'm losing everything past the half-inch mark.  I have 3/4 inch that is just white space.

Taking that same setting, and using multipage, and printing the pdf, the right side is lined up the same, and the left side is moved in 1/2 inch.  In other words, my 8 1/2 inch wide image has now been effectively shrunk to 7 7/16 inches wide.  Then the right 1/2 inch is cut off.  Then I get 5/8 inch of unprinted space on each side.  

This is infuriating!  Is there no clear, concise, readable explanation of how to do this?  Point me in the direction or cut and paste or something.  PLEASE!!!!!!!

Keith

---

