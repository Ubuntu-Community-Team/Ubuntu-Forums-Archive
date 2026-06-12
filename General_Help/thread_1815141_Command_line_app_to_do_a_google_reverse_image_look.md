---
title: "Command line app to do a google reverse image lookup?"
date: 2011-07-30
forum: General Help
---

### Post by sirchmeister on 2011-07-30
Some kind of app that would accept an input image and then run a search in the default web browser? Is anyone aware of something like this? I wanted to incorporate it in to the Nautilus context menu.

Thanks in advance.

---

### Post by AlphaLexman on 2011-07-30
> **sirchmeister said:**
> Some kind of app that would accept an input image and then run a search in the default web browser? Is anyone aware of something like this? I wanted to incorporate it in to the Nautilus context menu.

Thanks in advance.
Your Title states you require a command line solution, however your text desires a 'Nautilus' solution ??

The latest Google/Images page can accept 'drag & drop' images...

Have you tried that, or are you looking for another solution ??

---

### Post by sirchmeister on 2011-07-30
Basically I just needed a command line solution so I could use nautilus-actions to setup a context menu item that passes the filename to it and run a search in the default browser.

---

### Post by AlphaLexman on 2011-07-30
> **sirchmeister said:**
> Basically I just needed a command line solution so I could use nautilus-actions to setup a context menu item that passes the filename to it and run a search in the default browser.
How does google images come into play ??

You are not being completely clear on your objective!

Please specify.

---

### Post by sirchmeister on 2011-07-30
I want to be able to right click an image in Nautilus and go to a nautilus context menu action I have created to perform the google reverse image search.

---

### Post by Habitual on 2011-07-31
Then where does "Command line app" come into play?

I wrote a google search script ages ago, so it is do-able.

---

### Post by SoFl W on 2011-07-31
> **sirchmeister said:**
> I want to be able to right click an image in Nautilus and go to a nautilus context menu action I have created to perform the google reverse image search.

Is what you asking for is to be able to right click on the image, and "open with..." the name of your command line application?

Step 1: Locate image
Step 2: ?????
Step 3:  "open with" (a.k.a. profit)

By searching for "[Google command line]("http://www.google.com/search?&q=google+command+line")" for the solution to #2  you find that google has command line tools, but nothing for their image searches.
[B]
EDIT:[/B]
Firefox can open up from the command line using:
firefox [http://ubuntuforums.org](http://ubuntuforums.org)

**EDIT2:**
The problem is that google uses a script to upload the image and then process it.  During the process it gives the image its own unique file name so even passing the filename in a url wont work.

---

### Post by sirchmeister on 2011-08-02
> **Habitual said:**
> Then where does "Command line app" come into play?

I wrote a google search script ages ago, so it is do-able.

I wanted to be able to do reverse image searches on pictures I find in nautilus by right clicking on them. A command line program would just come in to play because it is what I would use to setup the context entry with Nautilus Actions. It could be a script though as long as I could pass it parameters. I imagine such a script/program would need to upload the image to the new google reverse image search:

[http://images.google.com/](http://images.google.com/)

---

