---
title: "Can't delete partition (gparted)"
date: 2011-07-02
forum: General Help
---

### Post by diebodie on 2011-07-02
Howdy!

So I've installed ubuntu on a external usb hard-drive on a 25gb partition. Anyways, whilst I was upgrading my packages, my computer shut down and booting from that partition became impossible. I've tried recovering it using a live cd but it just wouldn't give. So now I'm booting from a mint live cd (testing it out) trying to delete the partition to make space for another. The problem is, it's ''locked'' and wont give me the option to do anything. I tried manually deleting all the files but the ''delete'' option is grayed out... 

Any ideas? I'm almost positive there was some freaky sudo stuff I could do to make it work... Can't seem to remember though. 

Oh and when I checked the permissions, it says root, with read only being the only option (everything is grayed out).

---

### Post by sam_delta on 2011-07-02
Make sure the partition is not mounted. If it is mounted, you can unmount it from gparted by right clicking the partition and selecting "unmount"

sam

---

### Post by diebodie on 2011-07-02
Thanks for the reply sam. I tried that but I received the following error. 
> 
The enclosing drive for the volume is locked

Any other ideas?

---

### Post by sam_delta on 2011-07-02
does right clicking the partition and selecting "information" gives any aditional information?

sam

---

### Post by diebodie on 2011-07-02
Figured it out. Used unmount -f and it finally gave way. Stubborn bastard :P Anyways, thanks for the help! Didn't realise the drive had to be unmounted... 

cheers and thanks again!


edit: at the risk of sounding like a moron, how does one set the thread status to solved? Haven't been on these forums in ages....

---

### Post by sam_delta on 2011-07-02
glad it worked.

click on mark as solved under 'thread tools', just above the first post.

sam

---

