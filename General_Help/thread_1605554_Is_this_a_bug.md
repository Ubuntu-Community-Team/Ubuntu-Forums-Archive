---
title: "Is this a bug?"
date: 2010-10-25
forum: General Help
---

### Post by joeknoodle on 2010-10-25
Apologies if this is in the wrong section.

In Lucid / Gnome, I like to keep a link to a usually "saved as empty" text file in my panel. Sometimes I need to save this file when it contains text, and so just save it (duh).

The "problem" though is that somehow when it does contain text this file is picked up by Evolution as some sort of email message, so that when I just want to open that file as a normal text file, it goes through Evolution.

Is this a bug? Is there some way to resolve this while keeping that link in the panel?

---

### Post by WorMzy on 2010-10-25
Right-click on the file (not the shortcut), and choose Properties. Click the Open With tab and make sure that your text editor is selected.

[IMG]http://img594.imageshack.us/img594/8568/20101025180234329x338sc.png[/IMG]

If this upsets anything, then revert the changes and consider giving the file a different file extension.

---

### Post by joeknoodle on 2010-10-25
> **WorMzy said:**
> Right-click on the file (not the shortcut), and choose Properties. Click the Open With tab and make sure that your text editor is selected.

[IMG]http://img594.imageshack.us/img594/8568/20101025180234329x338sc.png[/IMG]

If this upsets anything, then revert the changes and consider giving the file a different file extension.

http Here's the SS:

[IMG]http://i321.photobucket.com/albums/nn393/joeyknuccione/Screenshot-EmptyTextProperties.png[/IMG]

Looks like I'm good on that part.

---

### Post by efflandt on 2010-10-25
Why don't you simply end the filename with the usual .txt that designates a text file?  Then, unless you set something else as a default for that filename extension, opening it would usually default to gedit and offer alternatives like Open Office, etc.

---

### Post by WorMzy on 2010-10-25
Okay, that's fine. I guess the problem lies with the shortcut. I'm guessing you created a launcher which opens a location? Like this:
[IMG]http://img828.imageshack.us/img828/4884/20101025190139366x158sc.png[/IMG]

If so, create a new launcher which opens an application. Set the command to

```
gedit "path/to/file"
```

[IMG]http://img843.imageshack.us/img843/5758/20101025190244368x173sc.png[/IMG]

That should remove any possibility of the file opening with Evolution.

---

### Post by edhplus2 on 2010-10-25
Something else to try: 

Does the file start with the word "From"? 
On my setup here, Ubuntu 10.10, if the text file starts with "From" it thinks it is an email message. It used to do this in Fedora also, so it isn't Ubuntu. 

Lower case "from" will be seen on my computer as a text file and open with the text editor.

It drove me crazy until I figured it out, because I had a lot of quotations, death notices for genealogy, etc., and I would put the source in the first line, like: "From the N.Y. Times" etc.

-- Ed H

---

### Post by joeknoodle on 2010-10-26
@ efflandt:

I try not to use files or extensions related to the OS that shall not be named, but a quick test indicates your solution works.

@ WorMzy

All I did was drag the file to the panel, I didn't create a launcher. I don't feel it necessary to create clutter for a file that would launch normally before (see below), but I do appreciate your response.

@ edhplus2

"Does the file start with the word 'From'?"

^That looks to be exactly what is causing the problem.
--------------------

So now that brings me to...

My understanding is that Evolution is "hardwired" into Ubuntu, is there any way I can delete it without having Ubuntu go bonkers?

Yes, I'd rather not have Evolution if it's going to break my links / shortcuts.

---

### Post by WorMzy on 2010-10-26
I'm not sure how creating a new shortcut and removing the broken one would create clutter. :confused:

I believe that you are able to remove any "evolution-*" packages except for "evolution-data-server". Open Synaptic (System -> Administration -> Synaptic Package Manager) and mark the other evolution packages for removal, but pay attention to what they will remove with them. If things like "gnome-panel", and "nautilus" are included in the list, then cancel the removal.

---

### Post by joeknoodle on 2010-10-27
> **WorMzy said:**
> I'm not sure how creating a new shortcut and removing the broken one would create clutter. :confused:

I likely misunderstood what you were getting at, so would apologize for any confusion there.

> 
I believe that you are able to remove any "evolution-*" packages except for "evolution-data-server". Open Synaptic (System -> Administration -> Synaptic Package Manager) and mark the other evolution packages for removal, but pay attention to what they will remove with them. If things like "gnome-panel", and "nautilus" are included in the list, then cancel the removal.
Thanks, I'll try that and see how it goes.

---

