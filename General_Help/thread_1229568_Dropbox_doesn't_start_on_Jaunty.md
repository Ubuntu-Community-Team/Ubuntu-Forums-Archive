---
title: "Dropbox doesn't start on Jaunty"
date: 2009-08-02
forum: General Help
---

### Post by bluelightav on 2009-08-02
If you want to run Dropbox (getdropbox.com) on Jaunty and it doesn't start and if you start it from the terminal (dropbox start -i) you get this error message:

The program 'dropbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadIDChoice (invalid resource ID chosen for this connection)'....

then follow link:
[http://deuified.blogspot.com/2009/04/get-dropbox-to-work-on-jaunty-jackalope.html]("http://deuified.blogspot.com/2009/04/get-dropbox-to-work-on-jaunty-jackalope.html")

[SIZE="5"]BUT[/SIZE]
This solution worked for me but ....

Don't do a killall nautilus or logout. Do a restart.

Then disconnect your computer from any network
Then start dropbox and then only connect the network. 
Then configure Dropbox
After the next restart is works fine on Jaunty 32 bit:D

---

### Post by punong_bisyonaryo on 2009-10-15
Thank you! Thank you! m(_ _)m

---

