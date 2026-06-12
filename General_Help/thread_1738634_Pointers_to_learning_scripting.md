---
title: "Pointers to learning scripting"
date: 2011-04-25
forum: General Help
---

### Post by thejameslang on 2011-04-25
Hi guys!

I have a project for my computer class, and I was a bit ambitious with my ideas and am wondering if I made a smart choice... oh well, I need to learn sooner or later anyway!

I'm a beginner when it comes to scripting but I'd like to learn more advanced stuff. When I say basic I really mean basic among all basic. To give you an idea I only know some simple HTML and Python.

The idea I proposed for my project goes as follows:

The challenge we were given is to create a spreadsheet of data from a website given to us. Points are given for creativity and simplicity in how we go about doing this.

After taking a look at the site (or rather, html files given to us), and with having dabbled with Python before, I came up with what I thought was a pretty good idea.

The pages of the "site" are just numbers. They go from 001-117 .html in terms of filenames. Their source code has some sort of table set up, and the information we are pulling off are easily found by the tags that precede them (the info, btw are the periodic elements). 

The tags are pretty obvious, and state pretty much what they are labeling.

My python knowledge is almost nonexistent but I figured that would be something Python would be capable of.

Why do I post this here?
I'm relatively new to Ubuntu too but keep hearing about bash scripts and such. Would this be even better? (Perhaps it's silly but I'd like to use Ubuntu to accomplish this)

Or is there an even better scripting method/language I should be using?

Could anyone give me some pointers in how I could accomplish this?
I'm really hoping to learn a lot from my first "real" scripting experience!:P

---

### Post by fdrake on 2011-04-25
you have to be more clear on the objective of this. Create a spreadsheet of data of a give website? what data do you need to extract?

---

### Post by thejameslang on 2011-04-25
Sorry, let me elaborate on that.

Real simple pages that simply have three fields:

Name:
Number:
Symbol:

There's a page for each element.

All I want to do is to have the web browser first go to 001.html, pull out what's necessary from the source, add one to the filename, and then proceed with 002.html, etc.

I think as a bonus we can figure out how to get it to filter out the nonmetals.

Oh and then this data should get into a spreadsheet somehow.

The only way I know how to do this personally is through Mac OS X's Automator... but I really wanted to use this as a chance to really get to know Ubuntu and scripting better.

---

### Post by conradin on 2011-04-25
php and curl. write a webbot to do it. I have some code on a home computer.

other ideas, if you already know the page, and what you want out of that page, write a macro with something like Imacros. Cant get much simpler than that. 

Or you could integrate bash scritps with curl, maybe use some crude parsing with sed. 

But Im not sure how to output directly to an xls from bash. Im sure it can be done, though I would prolly use csv, then convert to xls, cuz excel can read in csv files.

So Thinking PHP is the way to go, via a bot, I got to this guy's site:
[http://www.schrenk.com/nostarch/webbots/DSP_download.php](http://www.schrenk.com/nostarch/webbots/DSP_download.php)
which features some nifty wrappers for pretty much exactly what youre doing.
see: LIB_http.php


Are the pages linked on each page or do you just increment the url?
This sounds like fun!

---

### Post by fdrake on 2011-04-25
i don't want to be too specific since this is YOUR Homework but i will give you some hints and links if you need
lets say:

you can use a batch script to get the page from the Internet analyze it and process it in a file

command you can use :
wget - to download the page address on the disk
cat - to read the file(source code) and to write on a file
grep - to find lines with specif word you are looking for(or tag name in the source code)
for (( i=1;i>0;i++)); do { } - a for loop for the number of the pages of the site

[link of batch command lines]("http://linuxcommand.org/")
if you have questions or problems post them here

---

