---
title: "Top AIML interpreters for Linux?"
date: 2010-02-15
forum: General Help
---

### Post by Ulfgeir on 2010-02-15
Hey gang,

I'd like to start doing some work with AIML (artificial intelligence markup language), but I'm having trouble finding a Linux-friendly interpreter.  What are the top open-source interpreters that I could install under Ubuntu 9.10?

Thanks

---

### Post by Chronon on 2010-02-15
I don't know very much about this topic, but I did find a site that looks like it might be useful.

[http://www.alicebot.org/downloads/programs.html](http://www.alicebot.org/downloads/programs.html)

---

### Post by Ulfgeir on 2010-02-15
Thanks for the link.  The one that worked best for me was [COLOR=RoyalBlue]**[Program Q]("http://sourceforge.net/projects/qaiml/files/")**[/COLOR].  All I had to do was download it, extract the contents to a directory and then run the program.  Extremely easy to use under Ubuntu, and it seems to be a very straightforward and simple-to-use application as well.  I'd recommend it from what I've seen so far.

As for the other programs mentioned on that site, here are a few notes about them that might help others who are interested in getting involved with AIML scripting.


-**Program Z by Pandorabots** is a purely web-based bot hosting service.  And I'm looking for interpreter software that will run locally on my machine.  So that one's out of the running.

-**Chatterbean** is a dead link, and a quick search of the web didn't turn up a more recent site for it.  So that program may be defunct at present.

-**Program D** hasn't been updated in five years and doesn't seem to be compatible with the latest version of Java that runs under Ubuntu 9.10.

-**Charliebot**  doesn't seem to be a stand-alone interpreter, but rather an AIML bot designed to be run by such software which a person would have to obtain elsewhere.  So I'm not sure why the site even has that one listed on the interpreter page.

-**Program E** only seems concerned with running bots through a browser interface for web applications.

-**Program R** is another dead link, but this time I was able to find an active web page by searching.  Unfortunately, this project is still in the alpha stage and doesn't have any releases available to the public yet.

-**Program V** is another dead link, and a casual search failed to turn up any active project on the web.

-**Program P or PASCALice** appears to be Windows exclusive.

-**Program Y or PyAIML **appears to be little more than a bare-bones AIML engine with no user interface, which the author expects others to build upon for a more full featured experience.  In other words, I'd have to do a lot of work just to get the thing up and running like a normal, end-user program.

-**Program#** claims cross-platform compatibility, but I wasn't able to figure out how to run it under Linux.  For one, they only have one version of the files you need to download, rather than separate downloads for Windows and Linux.  And secondly, their page's link for Documentation goes to a dead page, so there aren't any installation instructions for reference.

-**Program N** seems to be Windows exclusive.

-**Project CyN** seems to be purely web-based.  It's a site that lets you create AIML bots and then have them hosted for random users to interact with.  There doesn't appear to be any sort of downloadable interpreter for offline development.

-**libAIML** might be a viable option for some.  However, I'd already found Project Q when I read about this one, so I didn't bother proceeding with the install.  Whereas Project Q was an extremely simple download-extract-run application, libAIML requires that the program (along with a separately downloaded package of utility files) be compiled from source and then installed.

-**J-ALICE** is a project currently undergoing a change in direction.  They don't have any recent or supported downloads available, only non-supported legacy versions.  So I shied away from that one.

-**RebeccaAIML** seems like a well-maintained project, but the Linux friendly side of it seems to be almost exclusively geared toward the Fedora Core distro.  For anything else you have to download source code, and even after spending a good hour trying to get the thing installed, all I had to show for it was a fistful of errors and unmet dependencies.  This one does not have a friendly Ubuntu install at present.

-**ICQza** is made exclusively for ICQ integration, so it's not a stand-alone interpreter like you would expect for offline local interaction.  Plus, it's not even available for download at present due to legal issues with ICQ inc.

-**Program M** isn't one that I delved too deeply into.  The description makes it sound like a fairly heavily involved installation that requires multiple dependencies, including the installation of SETL, an old programming language it's built with.

---

