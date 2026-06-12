---
title: "Libre Office Question/ Using Find"
date: 2012-06-09
forum: General Help
---

### Post by neu5eeCh on 2012-06-09
One nice feature of Google Docs is that if you search for a given word, every occurrence of the word will be highlighted in the document. Is there a way to reproduce this in Libre Office.

It's a useful way, in my case, to search for the overuse of the passive tense.

---

### Post by chocklet on 2012-06-09
In LibreOffice 3.5.3, you can select...

Edit > Find & Replace > Find All

In the Find & Replace window , there is a "More Options" box in the lower left corner

---

### Post by neu5eeCh on 2012-06-09
> **chocklet said:**
> In LibreOffice 3.5.3, you can select...

Edit > Find & Replace > Find All

In the Find & Replace window , there is a "More Options" box in the lower left corner

Simple as that. Staring me in the face. Beautiful. Thank you! ):P

---

### Post by NTL2009 on 2012-06-30
Confused.  I just looked at the 'more options' with find/replace, and I didn't see anywhere that it allowed one to highlight all the occurrences of the search term. Where is that?


I really like how my Chromium browser handles 'find'. The CNTRL-F dialog pops up and retreats when done, not taking up screen space. Every occurrence is highlighted, and it tells you how many occurrences there are, and shows where in the scroll bar. CNTR-G finds the next one, CNTRL-SHIFT-G goes backwards.

Is there a way to get this in LibreOffice, and the other document viewers (find seems really slow in evince)? I see that gedit works this way, pop up and go-away dialog, highlight all, CNTRL-G for next, it just does not show total occurances.

-NTL2009

---

### Post by chocklet on 2012-06-30
> I didn't see anywhere that it allowed one to highlight all the occurrences of the search term. Where is that?click the "Find All" box in the "Find & Replace" window.

Edit > Find & Replace > Find All

With no option selected, "Find All" will highlight all occurances of a search term.  "More options" provides more ways to search.  However, selecting an option might render the "Find All" box inoperable, e.g. selecting the "search for styles" option.

With the "Find and Replace" window open, the LibreOffice response to pressing "f" is curious.  The direction (next/previous) is selected in the "more options" window, but appears to be tied to the last direction choosen using the "find" toolbar.  I haven't found a way to search both directions (next & previous) using the keyboard only.

I am not aware of a way to use the keyboard to cycle through highlighted occurances with the "Find and Replace" window closed.  

There are at least two options that provide mouse click boxes to go to the next or previous occurance.  But both options take up screen space, but do not necessarily hide document text. 

One option is the "navigator", view > navigator.  With the "list box" off, Navigator is a smallish movable window.  The Navigator window can be located near the top of the LibreOffice window, overlaying the menu and toolbars and thus not overlaying the document text.  

The other option is the "find" toolbar, view > toolbars > find, which takes up screen space at the bottom of the screen.

There could easily be more options.

To get a word count of just a selected word, highlight all occurances (Find All), then select 
tools > word count.


LibreOffice is capable but not warm and cuddly.  My "favorite" word processors, over the years, have been simple.  I have to admit, however, that the most important word processors in my life, that offer the power to deal with lengthy and complex documents, have been the heavy weights.

---

### Post by NTL2009 on 2012-06-30
Thanks **chocklet**, that does work, but as you say, there are a lot of limits. I did see that if I try to go to the next/previous it drops all the highlighting on the "find all". 

It just works so well in Chromium, I use it to find specific terms that I'm looking for, and I pretty much see instantly if there are more/fewer occurrences than I expect I probably need to try a different term. Going to word count is clever, but not as handy as just having a 3/37 pop up as you CNTRL-G.

Maybe this should be a feature request to the LibreOffice group? I guess I'll take a look into that later.

-NTL2009

---

