---
title: "Desktop search does not work in Ubuntu 11.10"
date: 2011-10-12
forum: General Help
---

### Post by reablom on 2011-10-12
It seems the search function in the dash does not work as it's supposed to.
When I search for a file I know for sure is in my home folder the result turns up empty. Searching for programs (e.g. GIMP) works fine, but files can only be found if they have been opened recently.

When I look at the desktop search settings it says "strigi service not running".
The tick box "Enable strigi desktop file indexer" is enabled.

Any ideas? I would prefer to use the Ubuntu Desktop search, but if it doesn't work I'll have to keep using Google Desktop....

---

### Post by dFlyer on 2011-10-12
Just tried it on my 11.10 desktop and the search works for both programs and data files. Not sure whats causing your problem. Have you tried opening a terminal and running the following command if this is a new recent install:

sudo updatedb

---

### Post by reablom on 2011-10-12
tried it, no result.

Desktop Search is still unable to find files I know for sure are there.

---

### Post by reablom on 2011-10-14
Bump

---

### Post by phibxr on 2011-10-14
> **reablom said:**
> It seems the search function in the dash does not work as it's supposed to.
When I search for a file I know for sure is in my home folder the result turns up empty. Searching for programs (e.g. GIMP) works fine, but files can only be found if they have been opened recently.

When I look at the desktop search settings it says "strigi service not running".
The tick box "Enable strigi desktop file indexer" is enabled.

Any ideas? I would prefer to use the Ubuntu Desktop search, but if it doesn't work I'll have to keep using Google Desktop....

I've actually never had it working. No idea whether it should be working or not. Searching for any part of a file name I have in any of my directories returns no result at all, while 'locate' in a terminal finds them just fine.

---

### Post by Is Mise on 2011-10-14
Dash file search uses Zeitgeist to find files, so unless you've opened/worked on a file with a Zeitgest-supported program it won't show up in your search.

---

### Post by kranezor on 2011-10-16
bump!
I have the same problem
but you just open terminal and type unity --reset

cheers :p

^
 l
 l
I am sorry of my reply above
to still has the same problem
those command not to fix them

---

### Post by autofyrsto on 2011-10-17
[QUOTE=kranezor]I have the same problem
but you just open terminal and type unity --reset[/QUOTE]
This actually solved my similar problem, which was that my dash would not find any applications. It found some files okay, but no applications. I had to open a terminal and look up the command whenever I wanted to start a program that was not in the launcher. It was very annoying, until I typed "unity --reset" as per this suggestion. It solved my problem, but also changed some other settings, such as the size of the icons in the launcher. I think those changes will be easy to restore as I find them. The main thing is that I am glad the dash now finds my applications! Thanks!

---

### Post by WB0HYQ on 2011-10-20
The command "unity --reset" completely blew me out of the water.  I lost everything including the top toolbar, the sidebar, and the terminal stopped responding.  All I have now is the desktop picture.  Nothing else.

This was my attempt to force Unity to find files I KNEW were in my file system.  Even using "*.*" couldn't find anything.

Ubuntu 11.10

Bill

---

### Post by autofyrsto on 2011-11-19
[QUOTE=autofyrsto]It was very annoying, until I typed "unity --reset" as per this suggestion. It solved my problem, but also changed some other settings, such as the size of the icons in the launcher.[/QUOTE]

Even my own celebration was a little premature. Unity resets, I get a fully functional dash, but the reset procedure continues running and doesn't seem to complete. I get many warnings and errors after "Setting Update "run_key". The errors go on for a long time. If I 'Ctrl-C' or otherwise interrupt the stream of errors, I get sent back to square one: everything works except for dash searches. I have not yet found a permanent solution.

*[COLOR="Red"]UPDATE:[/COLOR]* I did not paste this, but [these are the types of errors that I get]("http://pastebin.com/8aA1YwzJ").

---

