---
title: "I told Ubuntu to open cgi files by default -- help"
date: 2010-10-01
forum: General Help
---

### Post by L a r r y on 2010-10-01
I do not remember where I was accessing system preferences, but, since I edit cgi files in the Text Editor, I told Ubuntu to open them in the Text Editor by default when I double-click to open.

Perhaps question I answered was how I want executable scripts to be opened.

A week or so passes, and I am going to open a Hello World script on a web site, and Firefox wants to know whether to open it with Text Editor (Default) or Save As...!

I was not working in the Firefox screens, I was somewhere in System --> Administration or Preferences, because I wanted to amend the management of cgi scripts on the Gnome desktop.

I just reviewed my history in Terminal, and there is nothing there that relates to this problem.

I didn't discover the side effects of my change in the system's behavior until today when I placed a cgi file on my web site and tried to access it with the browser.

I checked another long-time cgi file that works within the website, but which isn't accessed directly, and it, too wanted to be downloaded and opened or saved.  These things executed in the past, but apparently not anymore since I told Ubuntu to not execute them.

Please direct me to the app I need to open to edit my Gnome preferences

Thanks!

---

### Post by sanderd17 on 2010-10-01
Can't you right click on a local cgi file and select properties, there change the default program to firefox.

---

### Post by WorMzy on 2010-10-01
What Firefox wants to do with the file has nothing to do with your choices in nautilus. If you're being asked what you want to do with the file, then you're not being served it correctly. CGI scripts should be run on a server, then the output from the script should be sent to the browser (in this case Firefox) in a way that the browser can understand it (for example, raw text or HTML); you should never be sent the actual CGI script.

---

### Post by L a r r y on 2010-10-02
Problem solved.  I was not actually downloading the script from the server, but instead the output of the script was being downloaded.  The text, "Hello World!" was saved to the hard drive as "world.pl" and opened in m6y text editor as a simple text file.

---

