---
title: "Bing as FireFox search? Help me restore Google"
date: 2011-05-03
forum: General Help
---

### Post by BobSongs on 2011-05-03
[SIZE=3][COLOR=DimGray]**System**[/COLOR][/SIZE]
Ubuntu Linux, Maverick, 10.10
FireFox: version 3.6.17
Mozilla Firefox for Ubuntu
canonical - 1.0

[COLOR=Red]**[SIZE=3]Problem:[/SIZE]**[/COLOR]
Until recently putting in some random word in the URL field defaulted to a Google search. Currently **Bing** replaces Google. I tested this by opening a new tab and typing in a random word in the URL bar (in this case, **fish**). A Bing search resulted (**[click here to see what I got]("http://www.bing.com/search?q=fish&pc=conduit&form=CONADR&ptag=AD035E5862ADD4C6DA1F&conlogo=CT2680363")**).

Normally we'd do **about:config** in the URL and change the **keyword.URL** from
```
http://search.conduit.com/ResultsExt.aspx?ctid=CT2680363&SearchSource=2&q=
```to
```
http://www.google.com/search?q=
```or to
```
http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=
```Tried this.

And it works... until the browser is restarted. Then the **keyword.URL** defaults right back to
```
http://search.conduit.com/ResultsExt.aspx?ctid=CT2680363&SearchSource=2&q=
```Has anyone managed to force FireFox to keep the **keyword.URL** from flipping back?

Thanks

---

### Post by BobSongs on 2011-05-03
After more investigation of the Internet, it's possible something put a low-level infection on my PC.

[SIZE=3][COLOR=Purple]**Solution:**[/COLOR][/SIZE]

[LIST]
[*]Exported my bookmarks to the desktop along with my weather settings.
[*]Opened the home folder, showed the hidden files.
[*]Located the .mozilla folder and renamed it .mozilla-infected.
[*]Started the browser to find it responds normally.
[/LIST]
Bing is no longer forcing its way up to the surface.

---

### Post by JOHNNYG713 on 2011-05-03
Have you tried changing your search engine at the search bar?

---

### Post by BobSongs on 2011-05-03
@JOHNNYG713

Thanks for the tip, however, "Bing" wasn't listed as a search engine within the list. It was a minor browser hijack, it seems.

In the image you attached, you pointed out the right side of the screen where the Google search lives. I normally used that nifty tool.

However, FireFox allows a **keyword** to do a similar kind of search within the browser's URL bar. When I type **imdb** and hit Enter, the **keyword** goes directly to Google, draws the likeliest website address ([http://www.imdb.com/](http://www.imdb.com/)) and offers that as a destination.

However, a hijacked browser will pull the user to Bing (or some other search engine). All attempts to manually restore the original lines failed. So, to restore things I

[LIST]
[*]backed up my bookmarks
[*]saved my Forecastbar Enhanced profile
[*]shut down FireFox
[*]renamed my ~/.mozilla folder to ~/.mozilla-infected
[*]downloaded and installed the usual few plug-ins I use
[*]restored my bookmarks and weather profile
[/LIST]
And I'm good to go. Firefox is now doing what it's always done.

It is of interest that when my browser's URL field area was hijacked, it was re-directed to Bing, Microsoft's sad Google clone.

---

