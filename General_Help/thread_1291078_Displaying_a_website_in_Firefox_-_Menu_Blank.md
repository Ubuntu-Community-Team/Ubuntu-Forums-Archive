---
title: "Displaying a website in Firefox - Menu Blank??"
date: 2009-10-14
forum: General Help
---

### Post by CrusaderAD on 2009-10-14
Check out the screenshot. When I bring up this site in firefox or opera, it doesn't display the far right menu option on the menu bar, but it will display it in Windows version of firefox. Any ideas?

---

### Post by macabrem on 2009-10-14
> **raptormanad said:**
> Check out the screenshot. When I bring up this site in firefox or opera, it doesn't display the far right menu option on the menu bar, but it will display it in Windows version of firefox. Any ideas?


I believe it is something to do with the page size or your font size.  

When I made my page smaller in Firefox by holding control on the keyboard and scrolling down with the wheel on my mouse, the link disappeared.  So, you might want to make the page larger, make your fonts larger, or just mess with the overall size however you want and the link should come back.

---

### Post by CrusaderAD on 2009-10-14
Thanks for the reply. I noticed how the other link / links will appear if I shrink the webpage the way you said. Do you think it's more of an issue with how the browser is displaying or how the website itself is written?

---

### Post by macabrem on 2009-10-14
> **raptormanad said:**
> Thanks for the reply. I noticed how the other link / links will appear if I shrink the webpage the way you said. Do you think it's more of an issue with how the browser is displaying or how the website itself is written?
 

Can you clarify - did that fix your problem or did you only succeed in making other links appear and disappear?


I think the issue is multifaceted.  I've designed websites, but I'm not a professional, so a lot of this is theoretical - but I think that sites are generally designed for certain "average" display sizes, fonts, etc.  Then individuals often change default sizes and fonts in their browser, or choose to let the website display as intended.  So, a site that was designed with default IE settings on a 15" monitor may or may not display correctly when settings are changed in the browser, or the browser itself is changed, to fit other screen resolutions.

---

### Post by mcduck on 2009-10-14
> **raptormanad said:**
> Thanks for the reply. I noticed how the other link / links will appear if I shrink the webpage the way you said. Do you think it's more of an issue with how the browser is displaying or how the website itself is written?

It's issue with how the web site is written.

If the page was correctly coded it would work with different font sizes without any problems, since that's what you always have to prepare for when making a web site. People use different font sizes and typefaces in their browsers, and different browsers have sightly different amounts of padding for many elements, so the page's layout must allow that. :)

---

### Post by CrusaderAD on 2009-10-14
Thanks for the replies. I'll have to do some more checking around. I see the same problem on Firefox using a Mac.

---

### Post by CrusaderAD on 2009-10-14
What about this.. Arial is a windows based font, so when LINUX can't read it or find the font, it defaults to something else. If it does this and the pixels are slightly larger / smaller in linux, couldn't that mess up the display?

---

### Post by mcduck on 2009-10-14
> **raptormanad said:**
> What about this.. Arial is a windows based font, so when LINUX can't read it or find the font, it defaults to something else. If it does this and the pixels are slightly larger / smaller in linux, couldn't that mess up the display?

Yes, that's exactly what's happening.. (apart from the pixels being slightly different size, since pixel's size depends on your display's size and resolution, not your OS or browser). Also it should be noted that even the same font doesn't render exactly the same on different systems. Font rendering is a lot more complicated thing than one might think. But if the page was designed correctly, it would allow each element to change it's size to fit whatever amount of space the contents of that element require.

For example the menu has to become larger as the font size increases. If it doesn't, it will break, since when creating a web page you simply can't expect the viewer to have the exact same font you'd like him to have, or to have his browser configured to use same font size or DPI setting as you do.

At their best, the font definitions on web pages are just suggestions: "If you have this font available I'd like you to use it here. If you don't have that font, then maybe you have this one? Or if you don't have that one either, I suggest using some sans-serif font here. Unless you want to use something else instead." 

That's all that can be done, since people use different operating systems that all have different fonts available, render them slightly differently, and display them using different kinds of monitors etc..

Any web page built to assume a certain typeface and font size *will* fail to render correctly for considerable part of viewers.

(of course it would be possible to just make sure every elemnt has enough extra space to allow for different typefaces, and then force font sizes by defining them in pixels. But that's bad design since it wouldn't, for example, allow a person with bad eyesight to use text large enough to read. And even then just about every browser has option to disallow web pages from defining typefaces and font sizes and instead force everything to show wit the exact font the user wants.)

edit: That page in your screenshot is actually fairly good one, apart from the menu. It tolerates a fair amount of font scaling without becoming a mess. If only the menu was made so that it could span over two lines, or increase in width, it would be very good. Now the menu breaks even with rather normal font sizes. But I know from experience that making that kind of horizontal menu work isn't easy, at least until we get proper support for scalable vector graphics on web pages. Still, the menu is something the page's creator should have easily noticed had he actually tested the page on different browsers & operating systems..

---

