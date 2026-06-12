---
title: "Ebay problem"
date: 2009-08-06
forum: General Help
---

### Post by coolclassic on 2009-08-06
Ebay has just changed there item page. Unfortunatly I can no longer view this in konqueror4.2.2.

Anyone else have this problem?

---

### Post by TeoBigusGeekus on 2009-08-06
Could you provide a link so that I can test it?

---

### Post by coolclassic on 2009-08-07
Here is link-[http://cgi.ebay.co.uk/Minolta-AF-50mm-f-1-7-Lens-X2-Teleconvertor-excellent_W0QQitemZ230363949598QQcmdZViewItemQQptZUK_CamerasPhoto_CameraAccessories_CameraLensesFilters_JN?hash=item35a2c2ea1e&_trksid=p3286.c0.m14]("http://cgi.ebay.co.uk/Minolta-AF-50mm-f-1-7-Lens-X2-Teleconvertor-excellent_W0QQitemZ230363949598QQcmdZViewItemQQptZUK_CamerasPhoto_CameraAccessories_CameraLensesFilters_JN?hash=item35a2c2ea1e&_trksid=p3286.c0.m14")

The problem occurs on every page I visit, Firefox works ok. For me it appears to be a konqueror issue.
I have java enabled

---

### Post by Soley on 2009-08-07
Although I don't use KDE, I do have Konqueror on my computer. (Have KDE to play around with)

It looks fine running it in Gnome. I'll log out and test it in KDE.

---

### Post by Soley on 2009-08-07
So I'm in KDE now & it still looks fine. What issue are you having? Is it just not loading at all. Does it look like the CSS is broken?

---

### Post by coolclassic on 2009-08-07
[IMG]http://lh6.ggpht.com/_DCpaduzGwWI/Snv-jEO2szI/AAAAAAAAAQM/UovIerbqAsU/s800/snapshot3.jpg[/IMG]

[IMG]http://lh4.ggpht.com/_DCpaduzGwWI/Snv-jcYzc-I/AAAAAAAAAQQ/MXTUQcs5Z64/s800/firefox.jpg[/IMG]

As yo can see detail information is missing from konqueror. Although I don't know much about css you may be right.

---

### Post by coolclassic on 2009-08-07
I was checking the source code for both konqueror and firefox and there is unique diffrences in the code i.e. konqueror has 56 lines less than firefox "fonts, spacing, ect all same".

A sample of code konqueror:
</script><div class="vi-cmb"><div class="itemHeader"><table cellpadding="0" cellspacing="0" border="0" class="area_nav"><tr><td valign="top"><span id="ngviback" class="sbt"><a href="http://photography.shop.ebay.co.uk:80/items/_W0QQ_dmptZUKQ5fCamerasPhotoQ5fCameraAccessoriesQ5fCameraLensesFiltersQ5fJNQQ_sopZ1?_nkw=minolta+-hood+-mc+-md+-rokkor+-adapter+-cap+-filter+-close&amp;_sacat=3323&amp;_fromfsb=&amp;_trksid=m270.l1313&amp;_odkw=minolta+-hood+-mc+-md+-rokkor+-adapter+-cap+-filter&amp;_osacat=3323#item3ca18120cd"><img src="http://pics.ebaystatic.com/aw/pics/uk/icon/iconLtArrow_20x20.gif" height="20" width="20" border="0" align="middle"></a><a href="http://photography.shop.ebay.co.uk:80/items/_W0QQ_dmptZUKQ5fCamerasPhotoQ5fCameraAccessoriesQ5fCameraLensesFiltersQ5fJNQQ_sopZ1?_nkw=minolta+-hood+-mc+-md+-rokkor+-adapter+-cap+-filter+-close&amp;_sacat=3323&amp;_fromfsb=&amp;_trksid=m270.l1313&amp;_odkw=minolta+-hood+-mc+-md+-rokkor+-adapter+-cap+-filter&amp;_osacat=3323#item3ca18120cd">Back to Search Results</a></span></td><td valign="top" class="pipe-cell"> | </td><td valign="top"><table style="margin-top: 0px;"><tr><td class="bc-label">Listed in category:</td><td valign="top"><div><div class="bbc-in bbc bbc-nav"><ul class="in"><li><a href="http://listings.ebay.co.uk/aw/plistings/category625/index.html?from=R11">Photography</a><span> &gt; </span></li><li><a href="http://listings.ebay.co.uk/aw/plistings/category3323/index.html?from=R11">Camera Lenses</a><span> &gt; </span></li><li><a href="http://listings.ebay.co.uk/aw/plistings/category30070/index.html?from=R11">For Digital SLR</a></li></ul></div></div></td></tr></table></td></tr></table><div style="padding-top:10px;"><div class="optin_hdr"><table width="100%"><tr><td><div class="optin_hdr_msg">We're working to make eBay easier to use.</div></td><td><div class="optin_links"><span style="font-weight:bold;"><a href="http://pages.ebay.co.uk/viewitem/tutorial.html" target="_blank">View our tutorial</a></span><img src="http://pics.ebaystatic.com/aw/pics/uk/s.gif" height="0" width="4"

Sample code firefox:

</script><div class="vi-cmb"><div class="itemHeader"><table cellpadding="0" cellspacing="0" border="0" class="area_nav"><tr><td valign="top"><span id="ngviback" class="sbt"><a href="http://www.ebay.co.uk/"><img src="http://pics.ebaystatic.com/aw/pics/uk/icon/iconLtArrow_20x20.gif" height="20" width="20" border="0" align="middle"></a><a href="http://www.ebay.co.uk/">Back to homepage</a></span></td><td valign="top" class="pipe-cell"> | </td><td valign="top"><table style="margin-top: 0px;"><tr><td class="bc-label">Listed in category:</td><td valign="top"><div><div class="bbc-in bbc bbc-nav"><ul class="in"><li><a href="http://listings.ebay.co.uk/aw/plistings/category625/index.html?from=R11">Photography</a><span> &gt; </span></li><li><a href="http://listings.ebay.co.uk/aw/plistings/category3323/index.html?from=R11">Camera Lenses</a><span> &gt; </span></li><li><a href="http://listings.ebay.co.uk/aw/plistings/category30070/index.html?from=R11">For Digital SLR</a></li></ul></div></div></td></tr></table></td></tr></table><div style="padding-top:10px;"><div class="optin_hdr"><table width="100%"><tr><td><div class="optin_hdr_msg">We're working to make eBay easier to use.</div></td><td><div class="optin_links"><span style="font-weight:bold;"><a href="http://pages.ebay.co.uk/viewitem/tutorial.html" target="_blank">View our tutorial</a></span><img src="http://pics.ebaystatic.com/aw/pics/uk/s.gif" height="0" width="4" border="0">|<img src="http://pics.ebaystatic.com/aw/pics/uk/s.gif" height="0" width="4" border="0"><a href="mailto:viewitem15-uk@ebay.com?subject=Comments on the new item page design on eBay">Send us your comments</a></div></td></tr></table></div></div></div></div><div style="margin-bottom:12px"><table width="100%" border="0" cellpadding="0" cellspacing="0"><tr><td nowrap="nowrap" width="100%" align="right"><span><span class="watchlinkSpan" id="linkTopAct"><img src="http://pics.ebaystatic.com/aw/pics/uk/s.gif" width="5"><a rel="nofollow" id="WatchYourItemLinkTop" class="watchLink" href="http://cgi1.ebay.co.uk/ws/eBayISAPI.dll

This is where the code starts to change konqueror seems to have code which is not in firefox (did search of firefox source)

Is this an issue with css?

---

### Post by coolclassic on 2009-08-07
Update: I used wget to download an offending page. I then opened with konqueror the whole page was displayed. The problem seems to be when down loading directly from ebay.

Any ideas?

---

