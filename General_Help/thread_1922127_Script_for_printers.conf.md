---
title: "Script for printers.conf?"
date: 2012-02-08
forum: General Help
---

### Post by vollz on 2012-02-08
Hello everyone! I'm new to ubuntu and a lil bit scripting, though I'm in a hurry to get a proper fix to my problem. Just want to point out this script has to be able to work on other computers aswell with ubuntu installed.

What i want to do is make a script that runs from the Desktop and goes to printers.conf in /etc/cups and edit a string and replace it. So far what I've done is creating two script files.

one that contains stopping cups, then using sed to replace the name i want and then booting up cups service again.

Doing so requires sudo command, so it asks for the password, so I type it in. After doing so the script fails doing what i want. So i created another script file that says "sudo ./script.sh" and it works. But i want it to be in the same file.

I'm sorry if it's fuzzy. 

Any help appreciated.

[Edit: Problem solved] 

// Vollz :D

---

