---
title: "Full Text Search"
date: 2011-01-03
forum: General Help
---

### Post by PatchesTheCaveman on 2011-01-03
What's the easiest way to search for a string in a text file in GNOME or on the console?  I used to do this in kfindfile back on KDE.

I'd like to avoid downloading something like desktop search if at all possible because I'm away for the holidays and stuck on a dialup connection.

Thanks guys!

---

### Post by noah++ on 2011-01-03
[grep]("http://www.panix.com/%7Eelflord/unix/grep.html") is the greatest once you master it.

---

### Post by stinkeye on 2011-01-03
This involves downloading a plugin for Gedit but it's pretty handy.
See here: [**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10248575&postcount=3[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10248575&postcount=3")

---

### Post by PatchesTheCaveman on 2011-01-03
> **noah++ said:**
> [grep]("http://www.panix.com/%7Eelflord/unix/grep.html") is the greatest once you master it.

How do you get it to search a whole folder of files including its subfolders, though?  And tell you which file it was in?  Can it even do that?

It's great when you're working with one file.  I use it to filter output from commands all the time.

---

### Post by stinkeye on 2011-01-03
Does
```
 grep -r "<string>" /directory/to/look_in
```
work?

---

### Post by PatchesTheCaveman on 2011-01-03
Wow.  Yes it does!  I looked through the command reference noah++ linked to and didn't see that either.  Guess I should RTFM more carefully.  :evil:

But, I already tried your other solution and that accomplished what I needed.  So, score two points for stinkeye tonight!  

Thank you all very much.

---

