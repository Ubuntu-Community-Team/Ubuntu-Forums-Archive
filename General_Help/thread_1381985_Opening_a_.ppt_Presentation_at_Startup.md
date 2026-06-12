---
title: "Opening a .ppt Presentation at Startup"
date: 2010-01-15
forum: General Help
---

### Post by /usr/home on 2010-01-15
A bit of background first, I work on Windows and OS X machines and Servers all day long, but I'm a bit of a noob when it comes to Linux so give me a break :).

Alright, so we have a customer that we plan on hooking up 2 Atom Nettops to TVs and having them display meal menus through powerpoint on them. They didn't come with Windows licenses and we are wanting to keep this cost low, so that's why we are doing this through Ubuntu. The plan so far is to ftp the .ppt file to each of the computers from a main Windows machine. I have the FTP servers up and running fine as well as VNC on both machines in case we need to access them. The path to the .ppt will remain static all the time so the filename and path will not change. Let's say it's called menu.ppt and it's located on the desktop of the user "user". I also have the 2 boxes automatically logging into the desktop. How can I launch this .ppt file on startup so that I don't have to touch the computer, just turn it on, and this menu.ppt will open and start playing? Or at the very least, open in OpenOffice or something of the sort and all the client has to do is VNC in and hit F5. Any ideas on how to accomplish this? Thanks in advance guys :).

---

### Post by spcwingo on 2010-01-15
You chould be able to write a small script and add it to autostart (under sessions in system>preferences>sessions).  Here's a template:

```
/bin/bash

sleep 7 && /path/to/ppt/menu.ppt
```

You can adjust the sleep timer if it tries to load before the desktop finishes loading.  ;)

---

### Post by audiomick on 2010-01-15
may I suggest using the open  office presenter format. The thing will be running in open office, which works quite ok, but why not convert to or use from scratch the native format?

Another alternative would be to use a slideshow .pdf. A video tech colleague told me recently that he encourages this, as it excludes the possibility of formats getting mixed up.

---

### Post by /usr/home on 2010-01-15
> **spcwingo said:**
> You chould be able to write a small script and add it to autostart (under sessions in system>preferences>sessions).  Here's a template:

```
/bin/bash

sleep 7 && /path/to/ppt/menu.ppt
```

You can adjust the sleep timer if it tries to load before the desktop finishes loading.  ;)

So can I make this script in something like Gedit? What would I save it as? Like in Windows it'd be like a .bat, what would it be for Ubuntu? (Yes, I'm a Linux noob.)

EDIT: NVM, I figured out how to make the script. Just trying to figure out how to add it to the sessions.

@audiomick - 

This client is computer illiterate in all forms. They wouldn't even get how to change the format of a document type in PowerPoint. They are using PowerPoint 2007 on their XP machines. The simpler it is, the better.

---

### Post by spcwingo on 2010-01-15
> **/usr/home said:**
> So can I make this script in something like Gedit? What would I save it as? Like in Windows it'd be like a .bat, what would it be for Ubuntu? (Yes, I'm a Linux noob.)

Yes, you can use gedit to write the script.  As far as what to save it as...whatever name works for you.  :)  Linux in general doesn't use extensions to decide what to use to open a file.  Instead it uses headers (hence the /bin/bash part of the script).

---

### Post by /usr/home on 2010-01-15
> **spcwingo said:**
> Yes, you can use gedit to write the script.  As far as what to save it as...whatever name works for you.  :)  Linux in general doesn't use extensions to decide what to use to open a file.  Instead it uses headers (hence the /bin/bash part of the script).

OK, so I have the script made. I'm not seeing this sessions you are talking about. Do you mean Startup Applications? I successfully added the VNC server to my startup and that works great. Would I add this in a similar fashion or what? (Thanks for the quick and informative replies :) )

---

### Post by spcwingo on 2010-01-15
Yes, under "Startup Applications".  I'm still on hardy so the name in the menu must have changed.  You would add it just like you added VNC.  Just point the "command" part to the script...oops...I forgot to let you know that you have to make the script executable.  No biggie just open a terminal and input these commands:

```
cd /path/to/script/directory
```

Followed by:

```
chmod +x ./script_name
```

Alternately you can open your file browser (Nautilus), navigate to the script, right click the script, select properties, and finally tick the box next to "Allow executing file as program" under the Permissions tab.

---

### Post by /usr/home on 2010-01-15
OK, so here's what my script looks like:

```

#!/bin/bash
gnome-open /home/riverview/Desktop/menu.ppt
```

I edited the permissions to allow it to run and everything and it runs, but it opens and closes right away and doesn't launch the file. If I try the same command, gnome-open... in a terminal window, it opens right up. Is there something wrong with my script?

---

### Post by spcwingo on 2010-01-15
> **/usr/home said:**
> OK, so here's what my script looks like:

```

#!/bin/bash
gnome-open /home/riverview/Desktop/menu.ppt
```

I edited the permissions to allow it to run and everything and it runs, but it opens and closes right away and doesn't launch the file. If I try the same command, gnome-open... in a terminal window, it opens right up. Is there something wrong with my script?

The script itself looks fine.  I have no idea about gnome-open as I have never used it.  Does it work with openoffice?  You can alter the script so that Impress opens it like this:

```
#!/bin/bash

simpress /home/riverview/Desktop/menu.ppt
```

---

### Post by /usr/home on 2010-01-15
> **spcwingo said:**
> The script itself looks fine.  I have no idea about gnome-open as I have never used it.  Does it work with openoffice?  You can alter the script so that Impress opens it like this:

```
#!/bin/bash

simpress /home/riverview/Desktop/menu.ppt
```

Hey, I have the script working in startup and everything now. The command wasn't simpress, but I tracked down where Impress actually was located and put that in instead. It's working great now. One final thing, is there a way to launch it right into presentation mode? I want it to open the file, but then immediately present it without hitting F5. Is there a parameter or something to accomplish this?

EDIT: I have it working by naming it a .pps instead of a .ppt and it launches right into presentation mode. However, it starts on a black screen and you have to hit next for it to work. I want to skip this black screen and just go right to the first slide. I've played with the presentation and edited a bunch of things, but nothing is working. Any ideas?

---

### Post by spcwingo on 2010-01-15
I have no idea.  I've never tried to do that.  You might want to ask the guys at the OpenOffice forum.  One of them probably knows a switch to do exactly what you're wanting.  Here's a link to their forums:

[http://www.oooforum.org/]("http://www.oooforum.org/")

---

### Post by marshmallow1304 on 2010-01-15
> **/usr/home said:**
> One final thing, is there a way to launch it right into presentation mode? I want it to open the file, but then immediately present it without hitting F5. Is there a parameter or something to accomplish this?

> **man ooimpress]       -show presentation
              Starts with the given Impress file and starts the  presentation.
              Enters edit mode after the presentation.[/QUOTE]

I tried it with both .ppt and .pps and it works.

So,
```
ooimpress -show powerpoint.pp?
```

[QUOTE=/usr/home said:**
> I want to skip this black screen and just go right to the first slide. I've played with the presentation and edited a bunch of things, but nothing is working. Any ideas?
Install [xautomation]("apt://xautomation") and use xte to simulate a keypress that would advance to the slide, like so
```
xte "key space"
```
I'm not exactly sure how you would integrate that in your script, but I'm sure there's a way.

---

### Post by viva la vida on 2012-01-24
Hey gurus! I would like to do same as the starter of the thread: PC that opens powerpoint -file (located in our web server) fully automatically when the pc is turned on. And it should also play mms internet radio station similarly (hidden).

That mini-pc would be located in store's showcase, so it shouldn't open any "update now"- popups etc on the screen...

I'm totally noob with Linux :!: I really appreciate if someone could help me with this. :p

---

