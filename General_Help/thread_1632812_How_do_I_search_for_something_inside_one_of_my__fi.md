---
title: "How do I search for something inside one of my  files?"
date: 2010-11-28
forum: General Help
---

### Post by Handssolow on 2010-11-28
How can I search for one 6 letter word throughout all of my Ubuntu files?

Sounds simple but I've not found what I'm looking for. The bottom line is that I am wanting to clean up a file association in mime. Deeply sorry to say but I would have had more success if I were searching for this under XP. I must be doing something wrong.

Since I trialled a commercial company's map product under Wine somewhere in my system is still their name. Any gpx file I choose to download and the company's name appears in properties. Ggx files are also associated with Wine whilst an untainted PC in the house just has "Browse" as an "open with" option.

First things first, how do I find and delete this commercial company's name totally from any part of my system? How do I find their name in one or more of my files?

---

### Post by HermanAB on 2010-11-28
fgrep

---

### Post by oldfred on 2010-11-28
I think fgrep & grep are really the same - see man grep.

I used this to search for the word Megathread (exact spelling with capitals) in all the .txt files in my path and output the list to a text file.

grep Megathread ~/recover/txt/grub/*.txt > drs.txt

---

### Post by edhplus2 on 2010-11-28
I'm not sure if this will accomplish everything you are trying to do, but I think it will get rid of the file association problem.
Open nautilus and right click on one of the .gpx files. Choose Properties, then the "Open With" tab. Highlight the application you no longer want to be associated with the file, then click the Remove button at the bottom.
Or if you wanted to leave the application as one of the choices, then set the radio button for the  application you prefer, and then click on Close.

---

### Post by Handssolow on 2010-11-28
I am sorry to report edhplus2 that I have nothing selected with "Open with" in Properties yet Wine is still the default application which appears when I download a gpx file.

---

### Post by Handssolow on 2010-11-28
Sorry but I still need some more help. Below for example, Garbage = the commercial company's name I want to remove.

In the terminal if I enter: grep Garbage *.* nothing related to Garbage appears? I want to identify all of my files where Garbage appears, so is *.* appropriate?

---

### Post by nothingspecial on 2010-11-28
Not if you are doing it from your home

If they are system files, you need to do it from / (root)

Are you looking for files, or instances of a string (word?) within files?

If you are looking for files, then find will do it.

Post back.

---

### Post by Handssolow on 2010-11-28
Using my example where Garbage = the commercial company's name, I want to find the word Garbage in any file, anywhere in my Ubuntu system.

I tried a sudo grep Garbage *.* and got nothing.

My gpx files are associated with this commercial company's name but where in my system?

---

### Post by nothingspecial on 2010-11-28
> **Handssolow said:**
> Using my example where Garbage = the commercial company's name, I want to find the word Garbage in any file, anywhere in my Ubuntu system.

I tried a sudo grep Garbage *.* and got nothing.

My gpx files are associated with this commercial company's name but where in my system?

change ```
sudo grep Garbage *.* 
```

for

 ```
sudo grep -r Garbage /
``` 

The -r flag will search all files recursively

---

### Post by Penguin=) on 2010-11-28
[COLOR="Red"][/COLOR][SIZE="7"][/SIZE]

I thin its fgrep in the terminal.

---

### Post by Handssolow on 2010-11-28
I made some progress with sudo grep -R "Garbage" /home which found a couple of instances of "Garbage" in .conf and many in .wine which I've now deleted. There seems to be a warning coming up about a recursive process. 

My gpx files are still associated with "Garbage" application/x-wine-extensions-gpx which I'm assuming is a mime issue.

---

### Post by Handssolow on 2010-11-29
Thanks everybody.

It's a pity that Wine doesn't uninstall windoze programs more cleanly and return your Linux system to as was is. I've now finally managed to removed a company's name (=Garbage) being associated with any gpx file which I subsequently downloaded.

Also in Properties "Open With" no longer is re-sets to Wine.

What remains? Properties shows for a GPX Basic File Type as "application/x-wine-extension-gpx type (application/x-wine-extension-gpx)". This it's not a big deal for now.

The post below is dated but I'm not the only one who has this sort of issue.

[http://ubuntuforums.org/archive/index.php/t-51012.html](http://ubuntuforums.org/archive/index.php/t-51012.html)

---

