---
title: "gnome-terminal resizing and scrollback problems"
date: 2012-03-07
forum: General Help
---

### Post by squigish on 2012-03-07
Today I noticed a problem with gnome-terminal.  The weird part is that I am certain it didn't behave this way before, and I can't pinpoint any significant system change I've done since then.  

The problem has to do with the window size and scrollback.  When I open gnome-terminal, it has the default window size of 24 rows by 80 columns.  However, when I try to scroll up into the history, I can only see the first 6 lines (for a total of 30 lines).  If I generate new output, the oldest lines are no longer there.  Above the top visible line is a whole bunch of black space.  

If I increase the height of the window, I still only see 30 lines.  However, if I use a program like less, I can use the full height of the window, but only after first scrolling down and then back up to fill the space.  On subsequent runs of less, it behaves as expected.

My shell is /bin/bash, and I'm running Lucid 10.04 LTS, with Gnome.  I have switched my "scrollback" length in the gnome-terminal profile back and forth between 512 and unlimited, with no effect.

I'm totally perplexed, and I don't even know what would be good keywords to search.

Thanks for your help.

---

### Post by papibe on 2012-03-07
Hi squigish.

By default the scrollback limit is 512 lines. Have you modified your gnome-profile? or install any theme?

In any case, you can try a couple of things:

First, change back to the default profile in case you are using a different one. On the gnome-terminal menus:
```
Terminal -> Change Profile -> Default
```
Or if the default itself has been modified, you can always set the scrollback limit manually by going:
```
Edit -> Profile Preferences -> Scrolling (tab)
```
There you can set the field 'Scrollback' to whatever you need.

Hope it helps, and tell us how it goes.
Regards.

---

