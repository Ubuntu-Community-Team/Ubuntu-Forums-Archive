---
title: "OpenOffice.org Presentation problem"
date: 2009-12-22
forum: General Help
---

### Post by ph0bYx on 2009-12-22
Recently I have added fonts from my Windows box, the .ttf ones, and now when I try to open a presentation with OpenOffice.org it opens for ages, takes up 45-50% of the processor power, takes ages to change a slide and the font is different.
I have reason to believe that this problem is related to the newly added fonts because presentations worked fine in OpenOffice.org before I added them. 
I've installed PowerPoint Viewer which opens the presentations fine, but it's only a viewer and I can't do much more than just slide through the presentation so I need OpenOffice.org to work.

If it helps, to transfer the new fonts onto Ubuntu I've copied them all into:
/usr/share/fonts/truetype/
folder and refreshed the cache with:
fc-cache -f -v

Is there any way to fix the OpenOffice.org Presentation? Because I would like to keep those fonts but if the only option is to undo the addition of fonts could you please describe it in detail for I am still new to Linux.

Thanks in advance!

---

### Post by ph0bYx on 2009-12-23
I don't mean to sound annoying, but I would really like some help with this. Sorry for double post.

---

### Post by chaanakya_chiraag on 2009-12-23
That sounds like a weird problem...could there be some corrupt fonts that are slowing down the whole process??

---

### Post by ph0bYx on 2009-12-23
I'm not sure, all the fonts that I added where working fine while I was using them on Windows XP. Here's a picture of a presentation the way it looks now (took me about 30 seconds to open it):

[http://img132.imageshack.us/img132/5028/screenshotwf.png](http://img132.imageshack.us/img132/5028/screenshotwf.png)

Don't mind the language, it's Croatian. The font there wasn't like this one, it was Arial or something like that and now this particular font is on every presentation that I open.

---

### Post by chaanakya_chiraag on 2009-12-23
Check the Preferences in OpenOffice...Go to Tools-> Options->Fonts and make sure there is no replacement table.

---

### Post by chaanakya_chiraag on 2009-12-23
Also, try moving the fonts to ~/.fonts/.  I'm not sure if keeping them in /usr/share/fonts/truetype/ might have something wrong with it.  Also, I'm not sure, but it seems like some of those fonts may not be truetype...that might be another possible cause.

---

### Post by ph0bYx on 2009-12-24
I checked the preferences and there are no replacement tables. I even changed the font option below replacement tables to Courier New, that didn't work, same thing happens.
I moved the fonts to ~/.fonts/ which also didn't work. After that I browsed through the fonts folder and found a few with the .fon extension, removed them, tried again and same thing happens.
I even tried multiple presentation and they all have this error. 

And, strangely enough, after the testing I get this error with Mozilla Firefox:

[http://img691.imageshack.us/img691/2145/screenshot1l.png](http://img691.imageshack.us/img691/2145/screenshot1l.png)

The active tab doesn't show the text that it's suppose to, in this case "Google", and the links that drop down when you start writing the address in the address bar are missing the site name, like for example this thread's link would look like:
[http://__________.org/showthread.php?p=8543653](http://__________.org/showthread.php?p=8543653)
But after restarting Firefox it was all ok again.

This problem is really getting weird. Thanks for the help though, I appreciate it!

---

### Post by ph0bYx on 2009-12-26
Anyone got any more ideas? Bumping again, sorry.

---

### Post by chaanakya_chiraag on 2010-01-01
Sorry...I was on vacation :D Getting back to your problem...did you try COMPLETELY restarting OpenOffice?  Close all open documents and then **make sure to also quit out of the quickstarter**.  Then try starting it again and see if that fixes the issue.

---

### Post by chaanakya_chiraag on 2010-01-01
By the way, the quickstarter should be located in the upper right-hand corner of the screen with all the other icons.  Look for the OpenOffice.org logo.  Right-click on the logo and click "Exit Quickstarter".  No fear!  This will reappear the next time you start OpenOffice! :)

---

### Post by ph0bYx on 2010-01-01
I've restarted my computer and the first thing I did was to open that presentation and again the same thing happens. I'm not sure about that quickstarter, I've only seen that icon on Windows but never on Ubuntu. If it's any different or located somewhere harder to find, which I doubt but just in case, could you take a look at the screenshot of my browser and see if there's that quickstarter?

I did found the name of the font that's on all the presentations, but I did a whole system search and could find it. It's name is alien league.


Heh, I did run a search again while I was writing this and all the search found is an alien5.ttf font and I thought I'd delete that and try again. It worked, things are back to normal with the Presentation program. 
Now that the first part of it is done, the program is fixed, the next part is to find out why did this happen. So do you, or anyone else have any idea? I'll investigate further into this with the help of Google. I'll post if I find anything. 

Thank you chaanakya_chiraag for you time and effort, I appreciate it!
Happy new year!

---

### Post by chaanakya_chiraag on 2010-01-01
No problem!!  Glad to help!!  Happy New Year!! :). Now let's try try to figure out why this happened.  Check back tomorrow...I'll run some google searches myself, but my feeling is that somehow the default font got changed. Let me get back to you tomorrow.

---

