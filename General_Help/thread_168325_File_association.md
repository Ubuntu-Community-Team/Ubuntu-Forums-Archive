---
title: "File association"
date: 2006-04-30
forum: General Help
---

### Post by bnj on 2006-04-30
Hello,
Sorry if this question has been asked before. I tried to google it but i could not find a satisfactory answer.

I have some problems with real media files: If I downoad one on my desktop, it is considered as a "Text file". So when I double-click on it, I get an error message saying [1].  I have to right-click on it and choose "Open with real player" to make it work.

Besides, If i directly open a link on a real media file from firefox, instead of opening with realplayer, it opens with mplayer. Although the real player plug-in is installed. How can I change that?

Thank you.



[SIZE="1"]
[1] Cannot open journal_123020060430-122800-56k-001.rm The filename "journal_123020060430-122800-56k-001.rm" indicates that this file is of type "RealAudio broadcast". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.[/SIZE]

---

### Post by chettyk on 2006-04-30
[QUOTE=bnj]
I have some problems with real media files: If I downoad one on my desktop, it is considered as a "Text file". So when I double-click on it, I get an error message saying [1].  I have to right-click on it and choose "Open with real player" to make it work.
[/QUOTE]

Open the Nautilus file browser and navigate to the directory where the file is. Right-click on it. From the menu that appears, choose 'Properties'. Click on the 'Open With' tab. 

Since Nautilus appears to think your Real Media files are text files, the Real Media player will probably not be among the options listed in the tab. In that case, click on the '+Add' button. That will show all the programs that have been installed and you can then choose the Real Media player.

You can use this method to set the default program for opening various types of files.

---

### Post by bnj on 2006-05-02
Hello.
Thank you for your answer. But it does not work.
I still get the same error message as before, although "Real Player 10" is now selected as the default application in the Properties of the file. 

Is there no other way to change the default application of a file type, depending on its extension? I would like to know the real linux way (no click-way, but a file that I have to edit somewhere in /var or in /opt or in /lib or in one of these places).

thank you again,

Benjamin

---

