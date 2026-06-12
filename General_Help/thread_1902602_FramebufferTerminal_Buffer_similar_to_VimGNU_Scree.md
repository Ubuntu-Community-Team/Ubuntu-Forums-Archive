---
title: "Framebuffer/Terminal Buffer similar to Vim/GNU Screen"
date: 2011-12-31
forum: General Help
---

### Post by Rakarth on 2011-12-31
First off, apologies if this has already been asked however I'm completely unsure of what to search in relation to this question :)

I'm currently trying to write a small program to output simple lists of text to the terminal in a similar manner as Vim or GNU Screen. What I mean by this is that Vim for example does not scroll with the text that is entered, it appears to clear the screen and then write again. I understand the "clear" command for shell scripting however this just scrolls the terminal upwards. I suppose I am attempting to create a window within the terminal in which  my text is displayed and refreshed when new information is supplied and displayed.

Whether it matters or not I am using python as the language of choice for the program.

Again I apologise for the lack of clarity here. I'm unsure of the technical names of any of the features I'm trying to implement :oops:

---

### Post by The Cog on 2011-12-31
print "\x1b[H\x1b[J"
will clear the screen. It's actually two commands - cursor home and clear to end of page.

P.S.
Google "ansi escape sequences"

---

