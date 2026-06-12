---
title: "firefox bookmarks"
date: 2010-11-08
forum: General Help
---

### Post by hodad on 2010-11-08
I'm having a couple of problems with Firefox Bookmarks:
1. I cannot get the bookmark folders to sort by name under "organize bookmarks".  I can sort them OK, but there is no "save" button, so they revert to unsorted.

2. When I choose bookmarks, I get a tiny screen that is hard to navigate through.  How can I increase the size of the screen?

Thanks!

---

### Post by lovinglinux on 2010-11-08
> **hodad said:**
> 1. I cannot get the bookmark folders to sort by name under "organize bookmarks".  I can sort them OK, but there is no "save" button, so they revert to unsorted.

That is how it works. There is no save button. Once sorted they will remain sorted.

> **hodad said:**
> 2. When I choose bookmarks, I get a tiny screen that is hard to navigate through.  How can I increase the size of the screen?

Please post a screenshot or make a more complete description of what you are doing, since I don't know which window you are talking about and there are many ways to access your bookmarks.

---

### Post by hodad on 2010-11-09
Thanks for your response!

1. I tried it again several times: Under "Organize Bookmarks", I select all, and then Sort A - Z.  Result - it sorts, then I exit Organize Bookmarks, and I'm back to unsorted.

2. Can't get a screenshot; doesn't work when I'm trying to save a bookmark.  But here's what I try:
Choose "Bookmarks" -> "Bookmark this page", then I choose the rightmost of the two drop down buttons adjacent to "Folder".  I get a dropdown box that shows 8 lines.  I have probably 75 lines of favorites, and, of course, they are not alphabetized, so I have to scroll very slowly through all of the lines to find what I'm looking for.  It's such a pain, that I sometimes just give up trying to find what I'm looking for.

---

### Post by lovinglinux on 2010-11-09
> **hodad said:**
> 1. I tried it again several times: Under "Organize Bookmarks", I select all, and then Sort A - Z.  Result - it sorts, then I exit Organize Bookmarks, and I'm back to unsorted.

You need to select a top level folder. It won't sort the content of a folder inside another folder, just the folder itself.

> **hodad said:**
> 2. Can't get a screenshot; doesn't work when I'm trying to save a bookmark.  But here's what I try:
Choose "Bookmarks" -> "Bookmark this page", then I choose the rightmost of the two drop down buttons adjacent to "Folder".  I get a dropdown box that shows 8 lines.  I have probably 75 lines of favorites, and, of course, they are not alphabetized, so I have to scroll very slowly through all of the lines to find what I'm looking for.  It's such a pain, that I sometimes just give up trying to find what I'm looking for.

First, keep in mind you don't need to go through the menus, you can simply click on the star icon in the address bar to add/edit the bookmark for the corresponding page.

To solve your window size issue get OpenBook extension:

[https://addons.mozilla.org/en-US/firefox/addon/42/](https://addons.mozilla.org/en-US/firefox/addon/42/)

---

### Post by hodad on 2010-11-10
Step 1 worked! - I guess I was taking it one step too far and selecting all of the bookmarks in the folder, instead of the folder itself.

Step 2 didn't; I got:
"OpenBook 2.0.1.1 could not be installed because it is not compatible with Firefox 3.6.12"

Still, at least now I can find my bookmarks easier - Thanks!

---

### Post by lovinglinux on 2010-11-10
> **hodad said:**
> Step 2 didn't; I got:
"OpenBook 2.0.1.1 could not be installed because it is not compatible with Firefox 3.6.12"

You can force it to install by disabling the compatibility check. The easiest way of doing that is to use [Add-on Compatibility Reporter]("https://addons.mozilla.org/en-US/firefox/addon/15003/") extension. Keep in mind that any extension you try to install while using Add-on Compatibility Reporter, will be installed and enabled by default, even if they are really not compatible. What I mean is that some old extensions work without problems because they do not require any code changes, except the part in the extension manifest that determines which browser version is compatible. This is usually the situation with simple extensions that are not maintained anymore. But sometimes the extensions needs several changes in the code to work with your browser version or they cannot work at all, due to Firefox changes. In this case, it will throw errors and sometimes can cause other extensions to fail or even Firefox to fail.

That being said, I tested OpenBook with Firefox 4 and it seems to work properly. I couldn't see any errors in the console while running it.

After installing both extensions you will see a plus sign in the botton-left corner of the bookmarks dialog. Click and drag it to resize the dialog.

---

### Post by hodad on 2010-11-21
Thanks for the explanation; I'll give it a try (after I work out some more serious problems on the pc).:D

---

