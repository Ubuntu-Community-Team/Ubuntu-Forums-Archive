---
title: "get evolution email off defective hard drive"
date: 2009-11-11
forum: General Help
---

### Post by mikethegecko on 2009-11-11
Hi, I just crashed my ubuntu computer... I used the install disc to go in and get my pictures and documents but...

How can I get my email files? I was using evolution... Can I retrieve my bookmarks from firefox? I think I know where those files are but I have no permission to open that folder...

If these answers are here somewhere I couldn't find them...

Thanks

---

### Post by manoriax on 2009-11-11
I think all this stuff is saved in a hidden folder within the home-folder and in case you did not encrypt the data, you should be able to access it.

---

### Post by mr_steve on 2009-11-11
> **mikethegecko said:**
> Hi, I just crashed my ubuntu computer... I used the install disc to go in and get my pictures and documents but...

How can I get my email files? I was using evolution... Can I retrieve my bookmarks from firefox? I think I know where those files are but I have no permission to open that folder...

If these answers are here somewhere I couldn't find them...

Thanks

Evolution stores everything including local mailboxes into /home/<username>/.evolution

---

### Post by mikethegecko on 2009-11-11
I went to home, my user name, .evolution, mail, pop... when I get to the pop folder (where I think my email are located) there is an X on the folder and it says I don't have permission to open it. Same thing with the mozzila folder (where I think my bookmarks are located)... I haven't encrypted anything....

---

### Post by mr_steve on 2009-11-11
> **mikethegecko said:**
> I went to home, my user name, .evolution, mail, pop... when I get to the pop folder (where I think my email are located) there is an X on the folder and it says I don't have permission to open it. Same thing with the mozzila folder (where I think my bookmarks are located)... I haven't encrypted anything....

Are you running from the install CD? You will need root permissions to access those folders, since they are restricted to your user account on the broken system. Do this:

Open a terminal, from Applications->Accessories. Type in the following:
```
sudo nautilus
```This should open a new file explorer window, running as root. You should be able to access anything on your old hard drive now.

Edit: Also, I would suggest copying the whole .evolution folder. You can then drop that into your new home dir when you repair your system, and have all your mail, contacts, settings, etc restored. In theory, at least.

---

### Post by mikethegecko on 2009-11-11
Sweet! 

Thanks mr_steve! That helped me find everything... It looks like a bunch of text files but the information is still there - I'll take it!

Time to get a new hard drive and actually back stuff up this time...

---

