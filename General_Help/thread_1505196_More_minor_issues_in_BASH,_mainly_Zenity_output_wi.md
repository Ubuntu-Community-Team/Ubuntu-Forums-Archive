---
title: "More minor issues in BASH, mainly Zenity output with wget"
date: 2010-06-08
forum: General Help
---

### Post by Darkness Des on 2010-06-08
Ok. I'm trying to be independent here from asking every question I have about BASH, but frequently I can't find what I'm looking for on Google. This time it involves "for string in $(cat whatever.txt) ; do commands" type things. I have set up a script that pops up a Zenity window with a checklist of scripts, then checks for the names of those scripts in a temporary (by temporary I mean the last command in the script deletes it) file named .installer and downloads those scripts. When using wget in that for statement, it downloads the script. Then it downloads it again and adds an extension of ".1". Then it gets a weird file, "index.html?darknessdes.ucoz.com%2Fbin%2Fbackup.sh". It gets this file whether or not my backup script is selected, it makes no difference.

EDIT:
Ok, apparently it was a misstyped URL in the for statement for my backup script that got the weird one and the .1 extension from another incomplete for statement. However, it still downloads all files that I've written functions for whether or not they are in the .installer file or not. I could REALLY use some help here.

---

