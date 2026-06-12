---
title: "Firefox non-functioning"
date: 2012-04-29
forum: General Help
---

### Post by kd7sjt007 on 2012-04-29
I have done a fresh install of Ubuntu 12.04. I updated the system and then installed the Gnome Desktop Environment. Installed banshee music manager and imported my music to the new install. Tried to get on the internet to check email, and firefox gave me the error that it is already running and needs to be closed before you can open other browser.[COLOR="Red"]"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."[/COLOR]

The above in red is the exact error code I received. I tried doing a complete removal of firefox, I have tried reinstalling, I tried logging out and back in and even restarted the computer several times. 

I am Running Ubuntu 12.04 x64. My computer is an Hp Pavillion DV7-6135DX. It has 6 gigs of ram, and an intel i5 quad-core processor. Any help to get me back on firefox would be greatly appreciated. Thank you.

---

### Post by claracc on 2012-04-29
First of all, you have to kill firefox process in order to launch a new one:

In a xterm type ps -ef | grep firefox and kill by process number

Then perhaps you have to do a new profile for firefox

Next link: [http://support.mozilla.org/en-US/kb/Firefox%20is%20already%20running%20but%20is%20not%20responding](http://support.mozilla.org/en-US/kb/Firefox%20is%20already%20running%20but%20is%20not%20responding) gives you all the information to proceed.

---

### Post by kd7sjt007 on 2012-04-29
Thank you sir. the last suggestion is what it took to solve the problem. I appreciate your help. I now have firefox up and running. thanks again :)

---

### Post by claracc on 2012-04-29
You are welcome. Glad to help.

Please mark the thread as solved with "thread tools" in the upper right side of the page in order people can find solutios quickly.

---

