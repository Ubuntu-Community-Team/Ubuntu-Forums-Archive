---
title: "Script: Automatically add missing keys in Apt"
date: 2009-07-09
forum: General Help
---

### Post by Shifty13 on 2009-07-09
Hi all,

I'm still pretty new to Ubuntu, as I started with Intrepid, but I love fiddling with my stuff, so I finally decided to publish my first useful script. 

This is for all of you who are tired to go on the net to find the right command to add keys to the apt keyring every single time you add a repo. 'Cuz the gui is too easy.
I therefore finally present to you: Getkeys! (Isn't that a great and inventive name?)

**[COLOR="DarkOrange"][SIZE="3"]How it works[/SIZE][/COLOR]**

It just gets the ids of the missing keys that aptitude is whining about, and goes fetch all of them automatically on the ubuntu keyserver.
To run it just run ./getkeys or copy it in /usr/bin for ease of use. It takes no arguments.
For those who did not see, the file is attached.

**[COLOR="DarkOrange"][SIZE="3"]About[/SIZE][/COLOR]**

I did my best to comment every last bit of it for those who want to understand how it works, it's really easy don't be shy. I'm pretty sure it only uses standard programs so it shouldn't have any dependencies.
I tried to make it user friendly, so it's a bit talkative. Also I tried to make it fool proof, so it should not crash, and if it does the command ouputs its error like normal, so it should be easy to debug.

Hope you like it,

Titouan

---

