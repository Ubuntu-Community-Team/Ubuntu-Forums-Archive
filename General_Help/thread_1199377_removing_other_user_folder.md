---
title: "removing other user folder"
date: 2009-06-28
forum: General Help
---

### Post by SW90 on 2009-06-28
I added another user and called it guest, to see what that user would be able to do etc. And I decided that I didn't want to have that as an option.

After going to System > Administration > Users and Groups I deleted Guest, and when I checked to make sure i couldn't log in with it, I was not able to. 

But there is still a folder for guest in /home. 

How can I remove that?

I'm a fairly new Ubuntu user, running 8.04

---

### Post by michy99 on 2009-06-28
```
sudo rm -r /home/Guest
```Guest or guest whichever one it is.

---

### Post by [adult swim] on 2009-06-28
open up a terminal, applications>accessories>terminal and then paste in the following command
```
sudo rm -r /home/Guest
```hit enter and then type in your password and hit enter again.  it should be gone.

---

### Post by SW90 on 2009-11-15
thanks!

---

