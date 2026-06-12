---
title: "How to extract files in terminal?"
date: 2009-07-09
forum: General Help
---

### Post by razorboy5 on 2009-07-09
Hi 

whenever i try to customize I keep getting these instructions to "extract" the file in a certain place. And the place is always given in code (assuming that i'll have to find it using a terminal)

extracting in windows was simple enuf (since i used windows all my life) however i have no clud how to do so in Ubuntu. 

Atm i'm tryin to extract my theme into the Cairo-dock folder to get a new theme, how would i do this?

any examples or tutorial referrals would be appretiated

thx

---

### Post by unutbu on 2009-07-09
"Extracting" can mean different things depending on the type of file. 

Could you provide the link to the instructions?

---

### Post by razorboy5 on 2009-07-09
[http://www.gnome-look.org/content/show.php/%5BCairo-Dock%5D+Shiki-Colors+Themes?content=91831](http://www.gnome-look.org/content/show.php/%5BCairo-Dock%5D+Shiki-Colors+Themes?content=91831)

start getting confused from step 4

---

### Post by CSandman on 2009-07-09
> "Extracting" can mean different things depending on the type of file. 

The filetype is not really given in that link either.  My best advice if you're not very familiar with the CLI tools for some of the archive formats and just want to make it work is to use the gui.  Gnome has an archive manager which is a simple front end for a bunch of those tools.

From those instructions, you just need to download the archive containing the themes.  Next open up Nautilus and navigate to, and double-click on, the archive and the archive manager should come up.  Next it's just a simple matter of choosing the 'Extract to...' button (or some variation on 'Extract to') and choose the location (~/.config/cairo-dock/themes).

Hope this helps,

---

### Post by muteXe on 2009-07-09
I can't get to the file cuz i'm at work but can't you just browse to the file in nautilus, right-click on it and choose extract?

---

### Post by doas777 on 2009-07-09
looks like a .tar

```
tar -zxfv <tarfilepath> <outputpath>
```

---

### Post by CSandman on 2009-07-09
> **muteXe said:**
> I can't get to the file cuz i'm at work but can't you just browse to the file in nautilus, right-click on it and choose extract?

Yep that would work too.  There are so many ways to do the same thing.

---

