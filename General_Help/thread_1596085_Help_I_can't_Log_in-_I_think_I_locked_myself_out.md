---
title: "Help I can't Log in- I think I locked myself out"
date: 2010-10-13
forum: General Help
---

### Post by Damascushead on 2010-10-13
So I have the basic concepts of ubuntu, have been using it regularly for little over a year. I have recently decided to expand my knowledge and start teaching myself the inner workings.

In trying to learn shell scripting i added the line 
alias l='ls -l'         to my .profile

However I accidentally typed
 alias l='ls -l"        with a (") instead of a (')

I logged out because i wanted to log back in and test my first addition to .profile. However I can't log in anymore. I type in my password and the screen goes black, and a moment later it returns to the login screen.

I have another user account (let's call it "user 2") but couldn't access the .profile for user1 from user2.


Any help would be greatly appreciated. I am just a fool tryin to learn the basics.lol

Thanks:)

---

### Post by TeoBigusGeekus on 2010-10-14
I don't know what happened, but can't you reach the file with a live cd?

---

### Post by Damascushead on 2010-10-14
Hmmm...I am not sure. Excuse my ignorance, but how might that work? Will a live cd allow me to login as myself? or will it just let me navigate through a "blank" os?
 
Thanks for the response.
 
I will look into using a live cd

---

### Post by TeoBigusGeekus on 2010-10-14
With a live cd you should be able to navigate through your hard disks and do whatever you want.
Just make sure you don't touch anything in your file system.

---

### Post by Topsiho on 2010-10-14
When booting the computer you have a choice to start the recovery mode.
In this mode you are given the choice to go to the text mode as root.

As root you can try and find the .profile file in the /home/yourname map, and either modify this file (using vim) or, easier to do: remove this .profile file (which I don't have, so it is not really a necessary file).

Then try and reboot your system.

When you succeed to log in as yourself, you might try to undo your alias.

This is only a sketch of what I might try in this situation :)

Topsiho

---

### Post by Damascushead on 2010-10-14
Thank you both of you for your help. I will try these suggestions!:P

---

### Post by Damascushead on 2010-10-14
Thanks so much. I was able to get to the root command prompt and edit the file with emacs, but I had to boot up in recovery mode. Thanks for the help. Case closed

---

### Post by Topsiho on 2010-10-15
Great!

Topsiho

---

