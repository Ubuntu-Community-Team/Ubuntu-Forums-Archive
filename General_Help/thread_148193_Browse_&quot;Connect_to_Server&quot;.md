---
title: "Browse &quot;Connect to Server&quot;"
date: 2006-03-21
forum: General Help
---

### Post by sparty2809 on 2006-03-21
After you use the connect to server feature, how can you browse to that server say through gedit?  Where does it mount it?

Thanks.:confused:

---

### Post by harisund on 2006-03-21
I will give you an example of what I do .. 

Generally, when I connect to a server (let's say I am connecting to example.com)  I get an icon on the desktop. I double click on the icon, and it asks for password (if the connection requires one) 

Then it automatically opens nautilus and I can start browsing the server. 

Aren't you able to do this? What did you do? Could you outline your steps?

---

### Post by sparty2809 on 2006-03-22
Yes, I can do that.  I can browse fine.  What I want to do, is open up say gedit, and go to open and browse to that server.  Also, I want it so that users can write to the drive, not just root.  Does this make more sense?

---

### Post by kenweill on 2006-03-22
sudo chmod 777 <drive/directory> -R

---

### Post by NewWithoutClue on 2006-03-22
Doesn't seem to mount at all, it looks to me like a nautilus feature at most.
The file ~/.nautilus/metafiles/x-nautilus-desktop:%2F%2F%2F.xml contains information about the icons on your desktop that resemble a remote server.. so basically, their links.. nothing is actually mounted.

p01n7

---

