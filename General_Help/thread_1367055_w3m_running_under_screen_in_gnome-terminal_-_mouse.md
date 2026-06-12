---
title: "w3m running under screen in gnome-terminal - mouse fail"
date: 2009-12-29
forum: General Help
---

### Post by Esthellin on 2009-12-29
Recipe for Mouse Scroll Death (terminal commands will be in brackets)

Get one gnome-terminal.
Startup w3m with any site(w3m wikpedia.com)
Scroll the mouse wheel. The output moves up, giving the appearance of scrolling down the page. Good.
Click the mouse on the page. The cursor should change to this position, enabling links to be clicked and surfed.

Close down w3m.(Q)
Now:

Turn on screen (screen).
Startup w3m with any site(w3m wikpedia.com).
Scroll the mouse. The cursor now moves down the page, reaching the bottom and prompting for the page to be shifted. Not good.
Click the mouse on the page. Nothing happens. Double clicking will highlight the text as if wanting to copy it.

I have read up about screenrc edits with something called termcapinfo, but I can't find anything concrete.

Any suggestions?

P.S. $TERM when under screen is "screen" while normally it is "xterm". Does this contribute to anything?
P.P.S. All of the above also occurs if run in an xterm window rather than a gnome-terminal.

Note: Adding "termcapinfo xterm ti@:te@" to the screenrc file has the same visual effect as pressing ESC-[ - the scroll back in copy mode.
      Essentially I am looking for the correct w3m scrolling, as the scrolling in other programs works as intended.

---

