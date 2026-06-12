---
title: "gnome-default-applications-properties shows &quot;Python 2.7 Docs&quot; for browser"
date: 2012-07-02
forum: General Help
---

### Post by EntropyReduction on 2012-07-02
My default browser on ubuntu is firefox.

When an html page is invoked from another application (e.g. mail, keypass),  instead of the requested html page I get 

   file:: /usr/share/doc/python2.7/html/index.html

or I did until I unistalled python docs to see if that would make problem go away (It didn't; now ff still tries to go to page, get a 404).

If I double click on an html page in nautilus, no problem, page opens correctly.

gnome-default-applications-properties shows "Python 2.7 Docs" as a selected option,  but doesn't offer firefox as an alternative, only Opera and "Web Browser".

I've pored through about:config in firefox, and searched some likely folders (e.g. /etc) for a text string  "python2.7/html/index.html", found nothing.

Anyone have an idea how I can fix?

Many thanks

Alan

---

### Post by EntropyReduction on 2012-07-02
Searching with gconf-editor I found 
 
/desktop/gnome/url-handlers/http/command 
with value 
 
   firefox /usr/share/doc/python2.7/html/index.html 
 
changed to firefox "%s" and rebooted.  Problem still there.

Alan

---

### Post by EntropyReduction on 2012-07-10
Right, found the problem.

I had created several launchers in main menu to allow me to easily find documentation, e.g. 

    firefox /usr/share/doc/python2.7/html/index.html

I used
```

strace -f -e trace=file  - o $HOME/gnome-default-applications-properties.log gnome-default-applications-properties 

```to find out where gnome-default-applications-properties was going to find that "Python 2.7 Docs" was the name of my default browner.   Turns out it was looking in

  $HOME/.local/share/applications

which is where launchers seem to live.  I killed off all launchers referring to 

  firefox  file_name

and all was well.

Is this a bug?  Surely gnome-default-applications-properties shouldn't depend on what happens to be in main menu in completely different context?

Alan

---

