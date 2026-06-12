---
title: "Pasting tables from Chrome into terminal/irssi"
date: 2011-02-23
forum: General Help
---

### Post by anlag on 2011-02-23
I'm having issues with pasting text from tables in Chrome, into gnome-terminal. What happens is the text gets pasted, but there are no spaces between what was contents of different cells.

To take an example:

[http://en.wikipedia.org/wiki/Comparison_of_Android_e-book_reader_software](http://en.wikipedia.org/wiki/Comparison_of_Android_e-book_reader_software)

The first few cells of the first entry reads as such:

> Aldiko[1]	Yes	Yes	Yes

...when I paste directly into the browser. However, when I paste into a terminal, it shows like this:

> Aldiko[1]YesYesYes

This happens regardless of whether I copy/paste using mark and the middle mouse button, or whether I do it with Ctrl-C and Shift-Ins. It's particularly a problem when I want to paste things into irssi (terminal IRC client) and then need to go back and add spaces manually, or accept pasting a bunch of gibberish.

How can I paste table content into terminal/irssi without this inconvenience?


On a semi-related note, using Firefox, pasting table content into terminal works fine, and there is some space between the contents of different cells. However, that is also not unproblematic in irssi, since the spaces appear there to actually be tabs, each of which by default gets replaced by '/msg -Network user', as a shortcut to pm the last user I sent a private message. Pasting directly the above example into my irssi produces the following:

> Aldiko[1] -GalaxyNet someuser Yes -GalaxyNet someuser Yes -GalaxyNet someuser Yes


Edit: Chrome version is 10.0.648.82 beta, but this has been the case with all versions since last summer. Ubuntu version is 10.10, and I'm using GNOME.

---

### Post by blakep2 on 2011-02-23
You cant what you are coping is in table format.

Think about it this way..
go to the source page view-source:[http://en.wikipedia.org/wiki/Comparison_of_Android_e-book_reader_software](http://en.wikipedia.org/wiki/Comparison_of_Android_e-book_reader_software)

Go down to the code for the tables.

You should see why

---

### Post by anlag on 2011-02-23
Okay, I can see that what I'm getting when I paste into the terminal is just the table cell content, while the html tags get ignored. I don't see how it's impossible to somehow have a mechanism that translates the cell border to a whitespace character before it's pasted. Since Firefox seems to manage it (but with a tab rather than whitespace) I was thinking if there perhaps might be a Chrome extension, or some other way to do this. No luck so far though... but yeah, I really don't see how it would be impossible.

---

