---
title: "install gadmin-proftpd-0.4.0"
date: 2010-07-25
forum: General Help
---

### Post by chrismitt2002 on 2010-07-25
i want to set up a ftp site for a few buddies to grab some files from me but i have no clue how to install this gadmin-proftpd-0.4.0 it shows a gui so how do i get that im currently running ubuntu 10.04 w 3gb ram w a amd 9850 2.5ghz cpu on my server

---

### Post by robsoles on 2010-07-26
I don't use the GUI tools to administer this sort of daemon but I imagine I'll either help you or attract attention to your thread by trying!

open "System"->"Administration"->"Synaptic Package Manager" and pop 'proftp" into the search box.

Please verify for me that 'proftpd-basic' has a green fill in the checkbox and we can proceed from there.

---

### Post by chrismitt2002 on 2010-08-04
ok got that installed and ready to go on to the next step 

ps sorry about it takein so long to respond

---

### Post by chrismitt2002 on 2010-08-04
bump

---

### Post by chrismitt2002 on 2010-08-05
bump

---

### Post by robsoles on 2010-08-05
Sorry Chris, been a bit distracted.

have you used "Ubuntu Software Centre" or "Synaptic Package Manager" to install the gadmin-proftpd-0.4.0 package?

It is very likely that when you install it it will pull in all of the necessary bits including the package I directed you to grab in my first post - I was figuring you must have installed the GUI Admin tool for ProFTP and it didn't pull in the base necessities when I posted my first response.

When I pop 'gadmin' into search box of 'Ubuntu Software Centre' gadmin-proftpd is the second item listed, highlight it and click 'install'. When I pop the same into the 'Synaptic Package Manager' it is the third item listed and to install it you make the checkbox against it's name green again as before and press 'apply' in tool-ribbon of Synaptic.


To set up FTP access to your PC you might even get me, or someone else, to explain it here in a post/thread but I think you should at least try from one of the results of this Google search: [http://google.com/search?q=set+up+proftpd+in+ubuntu](http://google.com/search?q=set+up+proftpd+in+ubuntu) (Although they will very likely bypass gadmin to work in terminal)  first.

---

### Post by agenta on 2010-08-14
Getting frustrated here!  I think that I'm setting the users up correctly...but I can't find much documentation/instructions/how tos on this topic.  I can login my virtual users just fine but the directories aren't showing up.  I'm using a browser to login (firefox) [ftp://what.ever.the.addyis](ftp://what.ever.the.addyis) and I then get "Index of [ftp://what.ever.the.addyis/](ftp://what.ever.the.addyis/) with a link to "up to a higher level directory" that just keeps adding "../" every time you click it.  I've setup a directory for the user ( I thought ) but this is all that shows w/o fail everytime :(  Please help

---

### Post by robsoles on 2010-08-14
> **agenta said:**
> Getting frustrated here!  I think that I'm setting the users up correctly...but I can't find much documentation/instructions/how tos on this topic.  I can login my virtual users just fine but the directories aren't showing up.  I'm using a browser to login (firefox) [ftp://what.ever.the.addyis](ftp://what.ever.the.addyis) and I then get "Index of [ftp://what.ever.the.addyis/](ftp://what.ever.the.addyis/) with a link to "up to a higher level directory" that just keeps adding "../" every time you click it.  I've setup a directory for the user ( I thought ) but this is all that shows w/o fail everytime :(  Please help

[http://google.com/search?q=set+up+proftpd+in+ubuntu](http://google.com/search?q=set+up+proftpd+in+ubuntu) has lots of howtos, instructions and such like - admittedly I see some "noise" in results but still lots of clear enough instructions on the topic.

use filezilla instead of a browser to do FTP transactions - look for instructions relating to anonymous access to make sure that isn't getting in your way.

---

