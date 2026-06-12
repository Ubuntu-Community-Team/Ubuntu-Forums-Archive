---
title: "Bookmarks in Firefox 13.0 not working correctly"
date: 2012-06-27
forum: General Help
---

### Post by harecanada on 2012-06-27
Hi,
I am currently having a problem with Bookmarks in Firefox 13.0. When I want to save a bookmark, there use to be a drop down window that let you designate which folder you wanted to save the bookmark in. That window doesn't appear anymore. The bookmark is saved but not in a specified folder. Also, if I want to remove a bookmark, I use to be able to right click on it and get an option to delete it. Now if I right click on a bookmark I get bounced out of bookmarks all together and it closes.
Can anybody give me a clue as to what might be happening. I tried Firefox Help and didn't get anywhere.
harecanada

---

### Post by marinara on 2012-06-27
sounds like they removed the feature

---

### Post by Alan.Brown on 2012-06-27
I am using Firefox 13.0.1 and I have no problem in allocating bookmarks to folders or with deleting bookmarks.

I can suggest removing Firefox altogether and then re-installing it (using Synaptic Package Manager).   If that doesn't work try posting to the Firefox forum here - [http://support.mozilla.org/en-US/questions/new](http://support.mozilla.org/en-US/questions/new)

Alan

---

### Post by sgage on 2012-06-28
> **marinara said:**
> sounds like they removed the feature

They did not remove the feature. It sounds to me like your places.sqlite file is corrupted. It used to happen fairly often for me, but not in a while.

So, close Firefox, go to ~/.mozilla/firefox/(your profile) and delete places.sqlite. A new one will be created with all your bookmarks (they are backed up in the directory cleverly named 'bookmarkbackups'. You will, however, lose your browsing history and the little 'favicon' icons. They will come back as you visit each site.

If that doesn't fix it, then maybe try the reinstall.

---

### Post by harecanada on 2012-06-29
Thanks for the input everybody. I found that the drop down window to save Bookmarks to a specified folder is now found by clicking the star in the address bar and doesn't open when you click on "Bookmark This Page" 
Anyway that helps to keep things in order. So I'm good with that.
I'm finding Ubuntu 11.10 is a "glitchy" and I get some weird things occurring. My computer has frozen a couple of times and had to be restarted. That had me thinking there was an Ubuntu problem causing the Firefox glitch.
It should be fine now.
Thanks again,
harecanada

---

