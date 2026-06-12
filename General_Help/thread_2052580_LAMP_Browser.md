---
title: "LAMP Browser?"
date: 2012-09-03
forum: General Help
---

### Post by chriswt on 2012-09-03
[FONT=Times New Roman][SIZE=3]I installed Ubuntu 12.04 SERVER on a new HP Pavilion desktop PC.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]During install, I selected to install LAMP.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Therefore, on this install, do I have a Web Browser?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]And if so, what is the command to start the browser?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]If not, how do I get one installed?[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman] [/FONT][/SIZE]
[FONT=Times New Roman]Thanks![/FONT]

---

### Post by wojox on 2012-09-03
w3m should be installed by default.
```
w3m http://www.google.com
```

You would need to install x-server to get a graphical browser like firefox or chrome.

---

### Post by SeijiSensei on 2012-09-03
Typically you would be accessing the machine remotely with a web browser rather than running one on the server itself.  Apache provides an HTTP server that you can access over the network to view the HTML files or PHP output stored on the server.

---

