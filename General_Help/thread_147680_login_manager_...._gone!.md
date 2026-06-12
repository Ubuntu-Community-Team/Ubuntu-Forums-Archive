---
title: "login manager .... gone!"
date: 2006-03-20
forum: General Help
---

### Post by B3Nji on 2006-03-20
whats happend? i dont have a logon manager in admin anymore? and when i boot up me laptop it goes to text mode! i have to log in the do startx to get it all working?

how have i removed that? What do I do to get it back? 

cheers for your help guys

---

### Post by aggiechemist on 2006-03-20
Well I have had things like this before, so this is what I had to do. I can't promise its what you need, but my issue was similar:

I disable the startup of the GUI login manager (well, I did it on purpose).

It was on a Kubuntu system, so the command to start the login manager was kdm. (the K display manager).

To see if it even still works, login at the terminal and try typing kdm, or if you are on Ubuntu it would be gdm (I think).

Provided it still works, make sure it is in your boot sequence, Check that with rcconf (sudo apt-get install rcconf) and make sure gdm or kdm are marked to boot.

Good luck!

---

