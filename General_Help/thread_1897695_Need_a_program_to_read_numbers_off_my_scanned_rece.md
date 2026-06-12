---
title: "Need a program to read numbers off my scanned receipts"
date: 2011-12-19
forum: General Help
---

### Post by alkal0id on 2011-12-19
I've decided to become more business savvy so I can stop ending up broke all the time and start actually making money. First thing I'm doing is starting a budget to keep track of all my income and expenses. I downloaded a budget manager called gnucash but haven't tried it yet. From now on I'm going to keep every single receipt I get and enter them into this budget. Doing that manually would be very time consuming though, there must be a way to do it automatically. I have a scanner so all I need is a program that will detect numbers, letters and other characters in png files and converts them into text. I'm good with PHP so I can figure out how to sort out the text once I've got it so all I need is a program that can read letters and numbers off of image files and convert them into text format and save it in a text file or whatever. Anyone know a program that will do this?

---

### Post by kanikilu on 2011-12-19
I haven't personally needed to use any, but I'm guessing one of these OCR programs is a good place to start:

[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

There is also a PHP class for OCR, but I've never used it either:

[http://www.phpclasses.org/package/2874-PHP-Recognize-text-objects-in-graphical-images.html](http://www.phpclasses.org/package/2874-PHP-Recognize-text-objects-in-graphical-images.html)

Given the wide variety of receipt formats, I think it's going to be very time consuming (and easier said than done) to write a script to parse out common information (total, date, merchant, etc.), but best of luck to you!

---

