---
title: "Google Chrome bugs?"
date: 2009-09-23
forum: General Help
---

### Post by nortexoid on 2009-09-23
I should probably post this in the chrome mailing group, but anyway...

Is anyone else getting the following bugs using the latest chromium daily builds?

1. Downloads often finish prematurely so that the file is corrupt. (This generally happens with very large files.)

2. The Acrobat plugin doesn't work. Apparently nor does mozplugger. I can't view pdfs in the browser. It goes to a blank screen.

3. The drop down menus don't disappear after selecting an item. If there's a drop down menu and I click one of the options, it gets selected at the top but the menu stays open.

The first two are especially annoying and makes using Firefox regularly a must. Wish Chrome would get to a more usable state.

---

### Post by fragos on 2009-09-23
I never saw #1. As to #2 selecting a PDF file downloads it. Not what you want but IMHO workable since I deposit downloads on my Desktop making then a click away from viewing. I update Chromium daily as it's still in development and has daily releases. I use Epiphany as a backup solution.

---

### Post by nortexoid on 2009-09-23
Clicking on a pdf link does not always download the pdf, especially if the pdf is accessibly only through a javascript link (e.g. with academic journals accessed through a vpn or similar). Certainly NOT workable. It works as expected in Firefox.

I also update daily, but daily builds don't improve much or anything as far as I can tell. Changes to the problems I've mentioned will take time, I bet.

---

### Post by fragos on 2009-09-23
I've already decided that Chromium is my browser of choice. It's not complete or bug free yet but it works well enough to be my default browser. I don't mind occasionally running Epiphany when Chromium has trouble with a site. I use Epiphany to print for now. I look to daily releases more as stability improvements. We aren't even at an Alpha level release so there's no guarantee of completeness or stability. When I identify a problem that is reproducible I file a bug report with instructions and observations. Just saying something doesn't work isn't very helpful at this stage of development. To be honest I wouldn't recommend Chromium to anyone at this time unless I knew they were capable of dealing with the issues associated with using pre Alpha software.

---

### Post by nortexoid on 2009-09-24
Well, saying that something doesn't work **is** helpful at the development stage, provided it's reported as a bug. Anyway, this thread isn't intended as a complaint but more just wondering if the problems I'm encountering are specific to my installation. One thing that's annoying is that the acrobat plugin **used to** work but has since regressed, at least for me.

I was using Chrome as my default browser as well but I think I'll just stick with Firefox for the moment.

---

### Post by greyfox1 on 2009-10-03
I agree with your sentiments here, nortexoid. I found this thread while searching about the same issue. I don't see anyone else writing on the forums about it. I get the same behavior in both Chrome and Chromium-- trying to open any PDF file, such as [this one]("http://www.irs.gov/pub/irs-pdf/fw4.pdf") for example, just gets me a blank black tab. The PDF I linked to can just be downloaded via "save link as", but like you said this isn't always an option. Where I run into it is when trying to view a bill online via a javascript link. In this situation I have to use Firefox.

So, you aren't the only one seeing this.

---

### Post by nortexoid on 2009-10-03
greyfox1, that's good to know!

---

### Post by fragos on 2009-10-03
The blank tab happened but the PDF was also downloaded. The default download directory is your home directory. As a mater of course I always make my default download folder the Desktop.

---

### Post by nortexoid on 2009-10-03
On my system the pdf is not even downloaded. (I too have the desktop as my default download folder.) It's unfortunate, really.

---

### Post by greyfox1 on 2009-10-03
Same here: the PDF is not downloaded on my system. This was evident because I didn't get the typical download arrow animation or the typical download progress indication at the bottom of the window.  I also left the browser open for a while to make sure I wasn't just being too impatient. No dice.

EDIT: Just wanted to add that this is true of other file formats too, such as .doc (which works in FF).

---

### Post by fragos on 2009-10-03
Worked fine for me. I'm currently using 4.0.221.0 (Ubuntu build 27753) and have it's repository in my software sources.

---

### Post by greyfox1 on 2009-10-04
I have 4.0.220.1 from the Ubuntu repos (google-chrome-unstable package). What about you, nortexoid?

---

### Post by nortexoid on 2009-10-04
I'm using exactly the same build as fragos, 4.0.221.0 (Ubuntu build 27753). I'm using the chromium-daily ppa.

It used to work, so I'm not sure whether it was broken in a later build or I did something to my system that broke it. (The latter seems unlikely. I didn't touch the plugin folder or anything.)

---

### Post by rohitfeb14 on 2009-10-05
till the pdf bug is removed.. i guess chrome is far behind..

Well let's hope it gets resolved soon...

---

