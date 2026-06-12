---
title: "How do I find my files?"
date: 2011-04-29
forum: General Help
---

### Post by xdevnull on 2011-04-29
So I'm trying to believe in these lenses and so forth, but for whatever reason it is not working very well.  When I click the Files Lens and type to find a file, it doesn't find anything.  The only file it found was one I tracked down in Nautilus and opened by double clicking.  If I open it in Libre Office (as opposed to Natty), it will not appear in the File Lens.

What is the purpose of the File Lens?  To find files I've already tracked down?  I thought this was supposed to function in some way similar to gnome-do - that is: a more efficient way to find and open files.  Having me find them first is kind of cheating isn't it?

I realize that developers work in IDE's all day, but most people don't.  They are opening a series of emails, .doc's, .odt's, .pdf's, .jpg...etc, etc.  They are editing these files, sending, them, getting them back, editing them again, none of these files quite work together.  People want to be able to find their files by typing something they remember about them, like the file name, or folder they might be in.  

I don't see how natty has helped make this less irritating in my life - even a little.  I'm being so sincere right now.

---

### Post by r-senior on 2011-04-29
> **xdevnull said:**
> What is the purpose of the File Lens?
It's not a search, that's the most important thing to understand: It uses Zeitgeist to build up a picture of your recently used files and then gives access to common folders, i.e. Downloads and your Nautilus bookmarks.

You can also right-click for finer-grained selections, e.g. Videos. Again, these are based on your Zeitgeist history, they aren't searches.

Once it's had some time to build up a picture of what you have been working on, it makes it very fast to find things. The fact that the box is entitled "search" may well be a case for reporting a design bug.

If you want to do a traditional search for a file, hit the Ubuntu button or super key and type "search". If you search for files a lot, pin the search for files application to the launcher.

---

### Post by mc4man on 2011-04-29
> If I open it in Libre Office (as opposed to Natty), it will not appear in the File Lens.
That is true and a bit of a shortcoming in this Zeitgeist deal
Only files opened thru nautilus will show up, any file opened only thru any app's 'open' dialog  will not

edit: will have to amend that - some files opened only thru an app will show up, though with  others it will not

---

### Post by xdevnull on 2011-05-02
@mc4man - I don't understand that either - except that it is also true for the "recent documents" feature in gnome as well.  I don't see why it couldn't index the home folder or have some kind of setup where you could tell it what folders to keep an eye on.  

@r-senior: Thanks for the tip about typing search.  I love the search box - what is this 1995? LOL.

If I feel motivated I'm probably gonna open a bug.

---

