---
title: "Firefox Favicons Not Rendering"
date: 2009-10-29
forum: General Help
---

### Post by Loafers on 2009-10-29
Just installed Karmic.  Favicons usually appear after several clicks.  However, several hours and thousand clicks later the favicons still aren't showing up.

Also I have "Display windows and tabs from last time" enabled and when I restart firefox it only shows Homepage instead of my previous tabs....

What in the world is going on... ](*,)

---

### Post by High Roller on 2009-10-29
I'm having the same problem.
I had FF 3.5 installed on Jaunty and this issue wasn't present.

---

### Post by MockY on 2009-10-29
I don't have this issue at all. However, if the favicon is animated, it won't show the animation. Intrepid did.

---

### Post by High Roller on 2009-10-30
The bug is also seen on the ubuntu homepage under "[Take the Tour]("http://www.ubuntu.com/products/whatisubuntu/910features")" (see attached).  The favicon should be a dinosaur head for "Getting Started".

---

### Post by Loafers on 2009-10-30
> **High Roller said:**
> The bug is also seen on the ubuntu homepage under "[Take the Tour]("http://www.ubuntu.com/products/whatisubuntu/910features")" (see attached).  The favicon should be a dinosaur head for "Getting Started".

Nice catch.

Who do I report this bug to?  I reallly would like favicons.... :(

---

### Post by High Roller on 2009-10-30
Here's a workaround I just discovered...

1. Go to "View"--->"Toolbars"--->"Customize".
2. Check "Use Small Icons".
3. Uncheck "Use Small Icons".
4. Click "Done".

Now if you refresh the favicons by clicking on the items in your "Bookmarks Toolbar" to load each page it should restore them.

Pretty ugly bug though.  I'm trying to see if this was noticed before, guess I should have beta tested.  agh!

---

### Post by Loafers on 2009-10-30
> **High Roller said:**
> Here's a workaround I just discovered...

1. Go to "View"--->"Toolbars"--->"Customize".
2. Check "Use Small Icons".
3. Uncheck "Use Small Icons".
4. Click "Done".

Now if you refresh the favicons by clicking on the items in your "Bookmarks Toolbar" to load each page it should restore them.

Pretty ugly bug though.  I'm trying to see if this was noticed before, guess I should have beta tested.  agh!

I tried what you did, but it still doesn't work for me :(  

Off-topic, but I also noticed that when I have "Show my windows and tabs from last time" enabled, it does not show my windows and tabs from last time.

---

### Post by Lekensteyn on 2009-10-30
Rightclick Kickoff startbutton.
Select Menueditor.
Expand "Internet", and select Firefox (with the missing icon).

Press the "?" (icon) button, check Other icons.
Select Firefox3-5 and confirm it.

---

### Post by Loafers on 2009-10-30
> **Lekensteyn said:**
> Rightclick Kickoff startbutton.
Select Menueditor.
Expand "Internet", and select Firefox (with the missing icon).

Press the "?" (icon) button, check Other icons.
Select Firefox3-5 and confirm it.

What's the Kickoff start startbutton?

---

### Post by High Roller on 2009-10-31
Here's the bug report I just created.
Please confirm it!

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/466299](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/466299)

---

### Post by ikt on 2009-10-31
> **Loafers said:**
> Just installed Karmic.


Did you upgrade or fresh install?

Running ubuntu gold as a live cd, the 'getting started' favicon is updated when you go to the site, and bookmarking websites the favicons work on the menu or toolbar.

---

### Post by Loafers on 2009-10-31
> **High Roller said:**
> Here's the bug report I just created.
Please confirm it!

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/466299](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/466299)

Thanks!  Dunno how to confirm, but I just selected "This affects me too."

> Did you upgrade or fresh install?

Running ubuntu gold as a live cd, the 'getting started' favicon is updated when you go to the site, and bookmarking websites the favicons work on the menu or toolbar.

Fresh Install.

---

### Post by High Roller on 2009-10-31
I wonder if this is related to the missing "System" menu icons.
Or the missing "pull-down menu" icons from various programs.

---

### Post by Loafers on 2009-11-01
**[SIZE="3"]POSSIBLE SOLUTION: Oh My God...  I think I figured out why favicons aren't showing up.  I'm a privacy nut so I always have "Never remember history" set under privacy and when I set it back to "Remember history" and bookmared a page, the favicon appeared... ](*,)[/SIZE]**

---

### Post by TheNessus on 2009-11-01
favicons are ugly anyway, I use an add-on that completely removes them. prettier.

---

### Post by dopeking on 2010-04-29
hy everybody

had the same problem with the properties... doh!

---

