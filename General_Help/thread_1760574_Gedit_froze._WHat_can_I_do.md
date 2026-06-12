---
title: "Gedit froze. WHat can I do?"
date: 2011-05-17
forum: General Help
---

### Post by the duke7 on 2011-05-17
My Gedit froze with some information not saved. Is there anything I can do to unfreeze it without having to force quit?

I can move it around, minimize and maximize it but cannot do anything with the text. much less save it which is what I'm worried about. 

In the case I can't do anythin, is there a way to open gedit history to check unsaved files?

Also when I open another gedit with the command gksudo gedit a separate opens perfectly and I can use it, yet when I manually open one from applications it just adds itself as another tab to the frozen gedit. It's weird

any ideas?

---

### Post by mcduck on 2011-05-17
No, I don't think there's anything you can do.

In the future, you can set Gedit to automatically save a backup file at set interval (the option is in Gedit's preferences).

What comes to the other text editor working fine when launched with "gksudo gedit", that's because you are running it as another user (that's what gksudo does). Another user, another Gedit process so it has nothing to do with the Gedit proces you have already running (as your normal user).

---

### Post by wildmanne39 on 2011-05-17
> **the duke7 said:**
> My Gedit froze with some information not saved. Is there anything I can do to unfreeze it without having to force quit?

I can move it around, minimize and maximize it but cannot do anything with the text. much less save it which is what I'm worried about. 

In the case I can't do anythin, is there a way to open gedit history to check unsaved files?

Also when I open another gedit with the command gksudo gedit a separate opens perfectly and I can use it, yet when I manually open one from applications it just adds itself as another tab to the frozen gedit. It's weird

any ideas?
Hi, if everything else is working you could copy and paste it to libreoffice so you can restore it.

---

### Post by the duke7 on 2011-05-17
> **mcduck said:**
> No, I don't think there's anything you can do.

In the future, you can set Gedit to automatically save a backup file at set interval (the option is in Gedit's preferences).

What comes to the other text editor working fine when launched with "gksudo gedit", that's because you are running it as another user (that's what gksudo does). Another user, another Gedit process so it has nothing to do with the Gedit proces you have already running (as your normal user).

oh well. thanks anyway. I did manage to screencap some of the info but still lost some

Just used the automatically save files option. Where would I access those automatically saved files though?

---

### Post by nerdy_kid on 2011-05-17
in your /tmp/ folder I'm guessing.  I'd take a good snoop around there before you reboot the machine.

---

### Post by mc4man on 2011-05-17
> Where would I access those automatically saved files though?
I would think it's just autosaving the file you have open
The 'create back up before ...' will make a backup before saving in the same directory as file (filename~

---

### Post by mcduck on 2011-05-18
> **the duke7 said:**
> oh well. thanks anyway. I did manage to screencap some of the info but still lost some

Just used the automatically save files option. Where would I access those automatically saved files though?

It saves them in the same place where the original file is, but adds a "~" to the end of the filename (which makes them hidden files, so press ctrl-h in the file manager to show them).

---

### Post by MrMagik on 2011-08-25
Hi, what the first poster describes happened to me and I had multiple tabs open at the time with no way of switching between them with my mouse or keyboard, one of those open tabs held an unsaved document with important information and this is what I did to recover the data:

1. I selected a piece of text from my web browser.

2. I dragged the text from the web browser to the gedit window taskbar icon so that it maximized the gedit window.

3. With the left button still pressed and still dragging the text from the browser I moved it over the desired tab.

4. Once the desired tab was in focus I kept my mouse button pressed and moved it over the text pane.
 
5. Then I dragged the text up or down in the text pane without releasing the button so that I could scroll the text up or down.

6. Still without releasing the left mouse button I pressed the print screen key on the keyboard and then I pressed the enter key on the keyboard to save the screenshot.

7. I then kept scrolling down the right amount each time to capture and save the screenshot of the data that would fit on the screen.

8. Once I reached the end of the document text I released the left mouse button and it pasted the randomly selected piece of text I had selected from the webbrowser into the text pane.

9. I then forced quit the gedit application and lost the text but I managed to keep all the saved screenshots of the text for later retyping.

I hope this helps someone.

MrMagik

---

### Post by Fisher_ on 2012-06-12
> **MrMagik said:**
> Hi, what the first poster describes happened to me and I had multiple tabs open at the time with no way of switching between them with my mouse or keyboard, one of those open tabs held an unsaved document with important information and this is what I did to recover the data:

1. I selected a piece of text from my web browser.

2. I dragged the text from the web browser to the gedit window taskbar icon so that it maximized the gedit window.

3. With the left button still pressed and still dragging the text from the browser I moved it over the desired tab.

4. Once the desired tab was in focus I kept my mouse button pressed and moved it over the text pane.
 
5. Then I dragged the text up or down in the text pane without releasing the button so that I could scroll the text up or down.

6. Still without releasing the left mouse button I pressed the print screen key on the keyboard and then I pressed the enter key on the keyboard to save the screenshot.

7. I then kept scrolling down the right amount each time to capture and save the screenshot of the data that would fit on the screen.

8. Once I reached the end of the document text I released the left mouse button and it pasted the randomly selected piece of text I had selected from the webbrowser into the text pane.

9. I then forced quit the gedit application and lost the text but I managed to keep all the saved screenshots of the text for later retyping.

I hope this helps someone.

MrMagik

If you have almost literally saved my life (and 2 hours of precious, precious work). I'll try to find another way to do recover the file, given the same conditions (gedit freezed).

Thanks again.

---

### Post by overdrank on 2012-06-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

