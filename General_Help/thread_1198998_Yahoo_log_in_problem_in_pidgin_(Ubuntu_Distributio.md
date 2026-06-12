---
title: "Yahoo log in problem in pidgin (Ubuntu Distribution)????"
date: 2009-06-28
forum: General Help
---

### Post by dipaish on 2009-06-28
Yahoo ! Inc practically blocked all the Linux IM clients like pidgin,kopete. We all thought it might be some problems that has disabled us to log in but the story behind it is different. Yahoo has changed its login method which has made Instant messenger clients for linux to connect with yahoo protocol.

Anyways to every problem there are solutions. Follow the following steps to make your pidgin work with ubuntu 8.04 or ubuntu 9.04

I assume that you have pidgin installed already. Incase not please install pidgin using your favourite package manager.

Step 1 : Save this  key  (Right click and then select save link as )

Step 2 : Go to system >> Administration >> Software sources >>
enter the password if asked and then go to "Third Party Software " Click on the "Add" button and pase the line below depending on your ubuntu distribution.

Ubuntu 9.10

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

Ubuntu 9.04

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main

Ubuntu 8.10

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) intrepid main

Step 4 : Go to  "Authentication," click the "Import Key File" (this file is the one which you saved it just before ). Navigate to the location where you saved this file.

Step 5 : Update your system . Go to terminal and then click on sudo apt-get update or
 go to system >> administration >> Update Manager

Step 6: Close pidgin (if its currently logged in ) and then sign in your yahoo account.

---

