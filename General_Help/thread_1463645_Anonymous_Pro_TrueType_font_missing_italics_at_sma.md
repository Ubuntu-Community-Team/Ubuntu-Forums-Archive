---
title: "Anonymous Pro TrueType font missing italics at smaller sizes?"
date: 2010-04-27
forum: General Help
---

### Post by rps63ifid on 2010-04-27
I've downloaded and installed Mark Simonsen's excellent monospaced TrueType font Anonymous Pro (see [http://www.ms-studio.com/FontSales/anonymouspro.html](http://www.ms-studio.com/FontSales/anonymouspro.html)) and installed it on one of my boxes running 10.04, but have bumped into an oddity when trying to use that font at small sizes. In both gEdit and ActiveState's Komodo Edit text editors, it appears to be using a bitmapped version of the font at sizes less than 11pt and at those smaller sizes, any attempt to use italics versions of the face (it comes with both a regular-weight italic and a bold italic) results in the use of the corresponding non-italicized version (either regular or bold-regular). At sizes where it appears to be using a smoothed version, italics works fine with both weights.

Questions:
1. Is anyone else seeing this same behavior?
2. Is there a way to force the use of the smoothed version of the font at small sizes rather than the bitmapped version?
3. What's up with the italicized version at small sizes?

Thanks in advance.

-- 
/ron

---

### Post by rps63ifid on 2010-04-27
I know it's bad form to reply to my own thread, but I've found the following two statements on the above site that seem to offer some insight regarding the bitmapped version and the italics at small sizes:

Regarding use on Windows: "It's best to enable &#8220;font smoothing&#8221; (Control Panel > Display Properties > Appearance > Effects...). When font smoothing is set to &#8220;Standard&#8221;, the embedded bitmaps will automatically be used for the following point sizes: 7, 8, 9, and 10. For other sizes, or if you prefer non-jagged type, &#8220;ClearType&#8221; is the best choice."

Regarding italics and bitmaps: "While Anonymous Pro looks great on Macs, Windows and Linux PCs with antialiasing enabled, it also includes embedded bitmaps for specific pixel sizes (&#8220;ppems&#8221; in font nerd speak) for both the regular and bold weight. (Since slanted bitmaps look pretty bad and hard to read at the supported sizes, I chose to use the upright bitmaps for the italics as well.) "

That seems to answer my question #3, above, but leaves question #2 standing: is there a way to force the use of the smoothed version at small sizes on Linux, ala the author's description of using Window's ClearType?

-- 
/ron

---

### Post by wadkar on 2011-10-20
Did you find any solution ?
I downloaded the latest [Anonymous Pro 1.002  			(September 8, 2010 release).]("http://www.ms-studio.com/FontSales/AnonymousPro-1.002.zip") available from the official website, installed it. But I am facing the same problem. For font size < 11 , I see pixelated/bitmaps , i.e. ClearType/Subpixel smoothing seems disabled for the font rendering.
For font size = 11, the subpixel smoothing (aka ClearType) is active and the font renders smoothly but I see a very strange issue of horizontally flipped fonts (e.g. for "E" The distance between upper two horizontal bars is larger than lower two, i.e. to say horizontally flipped).
I am using it at font size >= 12, for which the font seems to render smooth and properly. Can someone please help me out here?

---

### Post by rps63ifid on 2011-10-20
I did... look for his Anonymous Pro Minus typeface at the same location ([http://www.ms-studio.com/FontSales/anonymouspro.html](http://www.ms-studio.com/FontSales/anonymouspro.html))... link is in the column on the right side of the page about two-thirds of the way down. After several notes back and forth with Mark Simonson, he has released this version and I've not had any problems at all. You'll probably want to remove Anonymous Pro before installing Anonymous Pro Minus.

-- 
/ron

---

