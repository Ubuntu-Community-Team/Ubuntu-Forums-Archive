---
title: "sorting of japanese files and folders"
date: 2010-02-19
forum: General Help
---

### Post by zbischof on 2010-02-19
Hey, today I was loading some Japanese music into Rhythmbox when I noticed some issues with sorting files.  There doesn't seem to be any sort of pattern that I could figure out, and it definitely does not follow the Japanese alphabetic order.

For example, in rhythmbox, I have one artist, &#12473;&#12493;&#12458;&#12504;&#12450;&#12540;, who has multiple albums in katakana.  The album listing at the top groups them together correctly (though they are not sorted in any way).  However, in the view list, the albums in mixed together and grouped together by track number.

I also noticed a lack of consistency in the terminal and file browser.  Which look like this in the terminal:

-rw-r--r-- 1 zsb739 zsb739    0 2010-02-19 12:36 &#12473;&#12497;
-rw-r--r-- 1 zsb739 zsb739    0 2010-02-19 12:37 &#12461;&#12511;
-rw-r--r-- 1 zsb739 zsb739    0 2010-02-19 12:36 &#12473;&#12459;
-rw-r--r-- 1 zsb739 zsb739    0 2010-02-19 12:46 &#12459;&#12511;
drwxr-xr-x 2 zsb739 zsb739 4096 2010-02-19 12:52 &#12511;&#12489;&#12522;
drwxr-xr-x 2 zsb739 zsb739 4096 2010-02-19 12:54 &#12511;&#12479;&#12459;
drwxr-xr-x 2 zsb739 zsb739 4096 2010-02-19 12:51 &#12513;&#12524;&#12531;&#12466;
drwxr-xr-x 2 zsb739 zsb739 4096 2010-02-19 12:51 &#12467;&#12502;&#12463;&#12525;
drwxr-xr-x 2 zsb739 zsb739 4096 2010-02-19 12:51 &#12510;&#12508;&#12525;&#12471;
drwxr-xr-x 2 zsb739 zsb739 4096 2010-02-19 12:54 &#12510;&#12507;&#12454;&#12471;
-rw-r--r-- 1 zsb739 zsb739    0 2010-02-19 12:37 &#12473;&#12540;&#12497;&#12540;

and like this in the file browser:

&#12511;&#12489;&#12522; (folder)
&#12511;&#12479;&#12459; (folder)
&#12467;&#12502;&#12463;&#12525; (folder)
&#12510;&#12508;&#12525;&#12471; (folder)
&#12513;&#12524;&#12531;&#12466; (folder)
&#12510;&#12507;&#12454;&#12471; (folder)
&#12459;&#12511; (file)
&#12461;&#12511; (file)
&#12473;&#12459; (file)
&#12473;&#12497;  (file)
&#12473;&#12540;&#12497;&#12540; (file)

Now, in the file browser it looks like they are in order, however even someone who does not know japanese could see that &#12510;&#12507;&#12454;&#12471; and &#12510;&#12508;&#12525;&#12471; should be next to each other in the file browser.  In the terminal there isn't really any ordering at all.

Sorry if the problem is due to some obvious cause, but it seems like there isn't much for sorting Japanese alphabetically and I don't know the language well enough to browse Japanese forums.  I was just wondering why this order is all different and if there was a way to support sorting.

---

