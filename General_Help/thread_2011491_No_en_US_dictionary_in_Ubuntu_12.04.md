---
title: "No en_US dictionary in Ubuntu 12.04"
date: 2012-06-27
forum: General Help
---

### Post by L a r r y on 2012-06-27
I have several issues with Ubuntu 12.04 and the Unity Desktop, but I will focus here on the missing US English dictionary.  And the wrong **date** format as well.

I thought I had posted on this topic, but perhaps I started one and pitched it before I posted it.

I did a fresh install from a Live CD of 12.04, and if I remember, I didn't have to change anything to have American English and keyboard.  I did not find the standard American date format, "May 25, 2012" available.  Only the European "25 May 2012" format, or all numbers.

In all applications I have en_GB, with spell checker telling me I am wrong on "color" in favor of "colour" to name one example.

Doing battle with the missing spell check function in Firefox, unless I open up more tabs, I went in and specified en_US, but it is not on my machine because it still uses en_GB for my dictionary.


**Now where do I go to retrieve a US English dictionary?**
Please advise.

Any advice about the date format would be appreciated also.

Thanks!

---

### Post by L a r r y on 2012-07-01
Follow-up:  After going through the MozillaZine forum looking for Firefox support, I was advised to go into Addons and get a spellcheck dictionary.

I dug up the **_United States English Spellchecker 6.0_**, adorned with an American flag icon to its left.

Now at least I get a reliable spell checker, which seems to pop up every time I get into a multi-lined field such as the edit window on a Wiki or the edit window for writing this post.

I re-selected en_US in the place of en_GB in the Firefox config editor at about:config.  This because I was still being flagged with British spelling errors on American-spelled words like color, flavor and the like.

Even with several restarts of Firefox and checking the about:config for that en_US setting, I STILL get flagged because I forgot the U in those words.

At least the dictionary works so far every time it is called on, even if it is the wrong country/region.

Looking at my Add-ons Manager, there is no "Preferences" option for the dictionary, just a "disable" and "remove."

Looking at the configuration editor, the  line, **spellchecker.dictionary** is still **user-set string en_US**.

So I guess I'll look in the ad-bloated Software Center for some spellcheck tools.

---

### Post by L a r r y on 2012-07-26
Still dealing with British spelling here.  I seem to have half-corrected the issue in Firefox, by adding the add-on United States spellcheck dictionary, and my configuration still points to en_US.  But the rest of the software seems to have en_GB spelling rules.  Color, other words that end in -or instead of the British -our still get flagged, even here in Firefox.

The time format is still wrong, but I have found no answers.  Hoping there is someone out there who has seen the same issue, or can tell me what to apt-get install to fix this issue.

> **L a r r y said:**
> Follow-up:  After going through the MozillaZine forum looking for Firefox support, I was advised to go into Addons and get a spellcheck dictionary.

I dug up the **_United States English Spellchecker 6.0_**, adorned with an American flag icon to its left.

Now at least I get a reliable spell checker, which seems to pop up every time I get into a multi-lined field such as the edit window on a Wiki or the edit window for writing this post.

I re-selected en_US in the place of en_GB in the Firefox config editor at about:config.  This because I was still being flagged with British spelling errors on American-spelled words like color, flavor and the like.

Even with several restarts of Firefox and checking the about:config for that en_US setting, I STILL get flagged because I forgot the U in those words.

At least the dictionary works so far every time it is called on, even if it is the wrong country/region.

Looking at my Add-ons Manager, there is no "Preferences" option for the dictionary, just a "disable" and "remove."

Looking at the configuration editor, the  line, **spellchecker.dictionary** is still **user-set string en_US**.

So I guess I'll look in the ad-bloated Software Center for some spellcheck tools.

---

