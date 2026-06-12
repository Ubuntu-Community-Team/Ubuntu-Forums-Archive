---
title: "How Can I see Fonts in my browser exactly as in Windows?"
date: 2010-09-26
forum: General Help
---

### Post by aisajib on 2010-09-26
Please don't get bored at me because of too many posts on the same day. :) I'm just blown away with the quickness of this forum!

One thing I dislike about Internet surfing in ubuntu is its font rendering. I know, in many ways, ubuntu shows a more beautiful font. Even for my mother language, Bangla, Ubuntu is the best platform to see the most beautiful font.

But when it comes to English, a problem exists. The exact fonts (written in the stylesheet of a website) is not shown in Firefox (or any other browser) in ubuntu. Practically, I face problems because I develop some websites (blogs, to be more accurate). Plus, I like to read blogs with its real font. For example, the font of New York Times is great. It just gets me reading.

In Ubuntu, I see that font looking something like Times New Roman. Looks like getting back to old days.

See how this particular site (davidhewson.com) looks in windows xp [**Look in the Paragraph text**): 

[IMG]http://img684.imageshack.us/img684/3580/davidhewsoncomwinxp.png[/IMG]


The same site in windows 7:

[IMG]http://img805.imageshack.us/img805/7381/davidhewsonwin7.png[/IMG]


The same site in Ubuntu (after installing MS TrueType Core Fonts through Software Center) [**Look in the paragraph text comparing to the above one**]:

[IMG]http://img814.imageshack.us/img814/7715/davidhewsonubuntu.png[/IMG]


If you see closely, you'll see the win7 version looks better than ubuntu and xp while xp one looks better than ubuntu (for me, because that's the real font, possibly Georgia).

As I have already said, I have downloaded and installed MS TrueType Core Fonts but still no change. Is there anything I can do for my browser to show off the real fonts used in the CSS? I really don't like this. I want to see real fonts. :( :(

Help, anyone?!

---

### Post by Lateralis on 2010-09-26
For what it is worth, I much prefer the second font to the first one anyway. :P  The second one is more pleasing to my eye.  But each to their own!  

I guess you've already checked this, but now harm in suggesting it anyway... Check your Firefox preferences.  Edit -> Preferences -> Content.  Under fonts and colours, hit the advanced tab.  In there you can choose which fonts to use as defaults if the website doesn't specify any and there's a check box to allow fonts defined in the page's HTML/CSS.  Make sure that box is checked.

---

### Post by theozzlives on 2010-09-26
You can install the Windows fonts in your /home directory. Just create a folder named .fonts ans drop your desired fonts in there. NOTE: Since the "." indicates the folder is hidden, you may have to go view > show hidden files.

---

### Post by aisajib on 2010-09-26
> Check your Firefox preferences.  Edit -> Preferences -> Content.   Under fonts and colours, hit the advanced tab.  In there you can choose  which fonts to use as defaults if the website doesn't specify any and  there's a check box to allow fonts defined in the page's HTML/CSS.  Make  sure that box is checked.
That box is checked.

> You can install the Windows fonts in your /home directory. Just create a  folder named .fonts ans drop your desired fonts in there. NOTE: Since  the "." indicates the folder is hidden, you may have to go view >  show hidden files.

I have installed MS core fonts from Software Center. Do I still have to do this manually? :?

---

### Post by aisajib on 2010-09-26
> For what it is worth, I much prefer the second font to the first one  anyway. :razz:  The second  one is more pleasing to my eye.  But each to their own!  

The second screenshot is taken from Windows 7. You can make your windows xp show like that by: right click on the desktop > properties > Appearance > Effects. Here in the second drop-down menu, which is by default 'standard', change to ClearType. You will see the font like the second picture here.

But in both cases, it's windows showing the exact font. I'm trying to show the original font in Ubuntu as well.

---

### Post by HansKloss on 2010-09-28
I'm faced with similar problem, trying to display perfect fonts.

I checked the website that you mentioned and Windows indeed renders font Georgia which can be confirmed by using Firefox add-on "Font Finder" 

In some other thread I found zipped fonts directory that helped me a lot with website layout, however fonts still need some tweaking.

I will report back if get lucky with that.

---

### Post by SeijiSensei on 2010-09-28
If you really need to see them "exactly as in Windows," then I suggest you look into running VirtualBox and installing a version of Windows in a virtual machine.  

Are you running GNOME, or KDE (Kubuntu)?  You might try KDE if you haven't already; it has its own font renderer which you might find more appealing esthetically.

If you have access to a Windows machine, I'd recommend installing its fonts into Ubuntu directly.  Copy the fonts to a memory stick and use your desktop environment's font installer.  See if that's a better result.

BTW, Venice was the biggest disappointment for my daughter and me during our trip to Italy this past summer.  Had a decent Indian (!) dinner but paid a lot for it, and a nice lunch near the Parco della Rembranze.  I heard that Venetian restaurants had become a favorite investment target for Chinese gangsters looking to launder money.  My daughter went to use the bathroom during the lunch I mentioned and told me there were a couple of Chinese guys sitting in the back doing nothing while the Italian staff handled everything else.  Sure enough, our credit card receipt said the payee was a company with a Chinese name.

---

### Post by aisajib on 2010-10-01
Thanks. I've installed Mac theme on gnome interface and I'm happy with its font rendering. :) Makes me feel a real mac. ;)

Sounds like I should not plan for a trip to Venice. What about other parts of Italy?

---

