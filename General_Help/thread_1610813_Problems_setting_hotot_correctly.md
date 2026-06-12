---
title: "Problems setting hotot correctly"
date: 2010-11-01
forum: General Help
---

### Post by jasataco on 2010-11-01
I've got ubuntu 10.10 maverick meerkat installed on my computer and I want a Twitter client.
I've heard that Hotot was very good and I wanted to try it. I have already used Turpìal and it worked perfectly. 
The problem begins when I try to log into twitter with Hotot. I put the PIN code. Then it asks for user and password. (am I right?) But after that, it does nothing. I click again in Sing in with twitter and in the top of the window, appears a dialog: "Begin to OAuth..." AND IT DOES NOTHING!!.
When I click on Preferences to see if any settings are wrong, it appears a dialog saying: "Cannot Authenticate You! Please check your username/password and API base".
What must I do??
Thank you for your time :)

---

### Post by c0d3n9n3 on 2011-01-05
sudo add-apt-repository ppa:jimmyxu/hotot
sudo apt-get update
sudo apt-get install hotot

This is what worked for me. just run each of those lines in a terminal, and it should install.

---

