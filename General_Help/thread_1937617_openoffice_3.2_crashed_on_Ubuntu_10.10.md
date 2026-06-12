---
title: "openoffice 3.2 crashed on Ubuntu 10.10"
date: 2012-03-08
forum: General Help
---

### Post by alameenn on 2012-03-08
hello everyone!

yesterday, i had openoffice 3.2 suddenly crashed on me! here is the scenario i have every time i click the word processor app:

1. i get the welcome screen
2. then nothing! as if i did nothing!

now, when i try to open old documents made in openoffice, i get the following message: "due to an unexpected error, oppenoffice.org crashed. all files you were working on will be saved now. the files will be recovered automatically when oppenoffice is lunched again" something like this.

notes:
- i'm using Ubuntu 10.10
- i removed openoffice completely
- installed openoffice 3.3 (but still getting oo3.2 welcome screen and the same scenario happens every time i try to run it!!!)
- i can run openoffice from the terminal though!


need help please!

greetings!

-

---

### Post by lechien73 on 2012-03-08
Hi and welcome to the forums,

It may be better for you to individually uninstall each of the OpenOffice components, and then re-install it in its entirety.

You could also try removing your OpenOffice profile, to see if that helps. To do this:

[LIST]
[*]Open your home folder in the file browser
[*]Press Ctrl+H to view hidden files
[*]Locate the directory named *.openoffice*
[*]Right click on it, and **Rename** it to .openoffice_old
[*]Try restarting OpenOffice again
[/LIST]

---

### Post by alameenn on 2012-03-09
@lechien73

thanks for the quick reply. 

didn't know the profile name changing trick before. 

it worked well for me!

have a nice day :]

alameenn.

---

