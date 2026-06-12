---
title: "Backend failing to start after adding a capture card?"
date: 2011-09-03
forum: General Help
---

### Post by SamuelCB on 2011-09-03
Hello everyone. Ok so today I was watching the gadget show and on it they setup a PVR computer using mythbuntu and so decided to give it a go myself meaning I am a complete noob!

Ok so I have so far managed to install everything correctly and all my hardware seems to be picked up correctly however I am now begging to get problems. 

When I click on Watch TV in the frontend it says that there is no capture card installed, so I run the backend setup utility to find the place where you add a new capture card. When I go onto capture cards it picks up my Hauppauge WinTV PVR-150 [ivtv] card all ok and allows me to add it. So after doing this I exit the backend setup and I am prompted to run mythfilldatabase, which I do. Once that is run I then start the front end again but now receive an error saying (could not connect to the master backend server. is it running? is the IP address set for it in mythtv-setup correct?) So.... I go back to backend setup and check the database settings which are as follows:

Local backend
IP address: 127.0.0.1
port: 6543
status port: 6544

master backend
ip address: 127.0.0.1
port: 6543

I believe these are all correct as I only have one computer running mythbuntu and it is acting as a frontend and the backend so should be pointing to itself? Correct?

I hope this is enough info to get some help as I really want this to work. Thanks.

---

