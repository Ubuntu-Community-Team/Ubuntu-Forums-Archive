---
title: "Ubuntu Cant Recgonize Home Network"
date: 2009-07-02
forum: General Help
---

### Post by MiniManz on 2009-07-02
I have a home network where files are shared with one another. The network is named MSHOME and if I have a file shared on the network, I can access it through any other computer on the network, this is how I handle 99% of my files.

In Ubuntu it recognizes the MSHOME network but when I click to go into it it reads this message:

UNABLE TO MOUNT LOCATION
Failed to retrieve share list from server

I have shared files/folders on the network, so why is this not working?

New Ubuntu user here, I'd hate to have one hurdle block what has so far been a smooth ride.

---

### Post by mthalis on 2009-07-02
Did you install Samba?
Watch this 
> [http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

---

### Post by MiniManz on 2009-07-02
> **mthalis said:**
> Did you install Samba?
Watch this
I believe so, I used Synaptic Package Manager.

What is the terminal line to install it? Such as sudo etc. etc.?

---

### Post by mthalis on 2009-07-02
sudo apt-get install samba or write click your folder select sharing option ...

---

### Post by MiniManz on 2009-07-02
OK, I installed Samba and now there is a new network called WORKGROUP but I restarted and now the Windows network that those 2 networks were in wot even open up now.

---

### Post by mthalis on 2009-07-02
More guide available here.
> [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by MiniManz on 2009-07-02
Nothing seems to be working, I installed smbfs, I could see 2 the 2 networks again but I still can't access them.

---

### Post by mthalis on 2009-07-02
Try changing permision of sharing object.

---

