---
title: "Repeated entries in &quot;Open With Other Application&quot; List"
date: 2011-06-26
forum: General Help
---

### Post by Tony_Harrison on 2011-06-26
When I open the "Open with Other Application" option on the context menu, my list of applications is excessive. I don't mind having the listing of nearly every program on my machine. What IS bothering me is the repeated entries. For example, I have Archive Mounter listed twice (one with icon, the other not). I have Banshee Media Player 3 times, DivX Player 4 times and Internet Explorer(via wine) a whopping 12 times! Where are these repeated entries and how can I remove them? The IE entries take up almost a third of my whole menu.
I have looked through the files mentioned [URL="http://www.ubuntugeek.com/how-to-addremove-applications-from-open-with-window.html"]here: 

http://www.ubuntugeek.com/how-to-addremove-applications-from-open-with-window.html[/URL] 

but I was not able to locate these repeated entries.
Any help would be much appreciated. Thanks! :-D

---

### Post by howefield on 2011-06-26
Have a look in the /home/user/.local/share/applications folder.

Try removing (might be better to move/rename them in case you want to put them back) any wine-extension-*.desktop files.

---

### Post by ajgreeny on 2011-06-26
If you right click on a file and go to **Properties ->Open with** tab, you can delete applications from the list that appears.  See screenshot.

---

