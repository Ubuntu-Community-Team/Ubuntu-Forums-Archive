---
title: "Access firefox bookmarks without firefox running"
date: 2012-06-10
forum: General Help
---

### Post by ticket on 2012-06-10
Firefox has a reasonable bookmark manager, but a bookmarked page that is infrequently used can only be accessed by first running firefox and then choosing Bookmarks -> Show all bookmarks, and then finding and clicking on the bookmark.

This is a bit tedious.  I would like to have the bookmarks available to me to browse without having to start firefox.

One method is to place shortcuts on the desktop, kept in a hierachy of nautilus folders, mimicking the firefox bookmarks hierarchy. Unfortuately you lose the favicons for the bookmarks when doing that.

Another method is to use GLX /Cairo dock, which has a thing called stacks that holds shortcuts along with their favicons. You can drag the url to a stack to create a web shortcut. This sort of works, but stacks within stacks aren't so easy to manage.

Has anyone got a nice solution of accessing a bookmark and going to the web page without running firefox first?

---

### Post by black veils on 2012-06-12
the shortcuts is a good idea. a messy alternative (from my experience) is to export the bookmarks to .html   so everything would be on one long page.

or, use opera web browser to select certain folders to export to html, if firefox is your default web browser, then they will still open as usual.

---

### Post by ticket on 2012-06-17
I've been thinking of a way to get the shortcuts to show the favicon.

It might be possible to write a script that processes a shortcut, visits the website and extracts the favicon to a favicons folder.  

The shortcut is then altered by the script to point to the favicon image in the favicon folder.


Some interesting info here about getting favicons:
[http://g.etfv.co/](http://g.etfv.co/)

---

