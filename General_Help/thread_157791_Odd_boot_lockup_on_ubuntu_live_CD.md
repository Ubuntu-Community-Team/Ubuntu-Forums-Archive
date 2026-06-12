---
title: "Odd boot lockup on ubuntu live CD"
date: 2006-04-09
forum: General Help
---

### Post by JanHammer on 2006-04-09
Ok so I'll try to explain this as much as possible although it's quite simple. Everything starts up fine and goes through the process of loading ubuntu (y'know the black backround and image with a progress bar) then it finishes and right before you think things are alright it locks up with a blank screen and a frozen "_" in the top left.  PC spec time:

(eMachine T1221)
1.3GHZ celeron 100mhz FSB
512mb PC133 RAM
40gb IDE HDD
geforce 5500 PCI

If you don't think you can help me don't just shrug it off but reply, or else I'll be back assuming no one saw, it tends to happen.

---

### Post by nanotube on 2006-04-09
did you try hitting ctrl-alt-f1, to see if you can get to another terminal?

---

### Post by taurus on 2006-04-09
Could be a problem with your video card.  Try this.  Hold down <Ctrl><Atl> while hitting F2.  Log in with your username and password.  Now, you need to edit your /etc/X11/xorg.conf by
```

sudo nano /etc/X11/xorg.conf  <--  it's capital X and number eleven, X11...

```
Use your arrow key and scroll down to the section about the Device, your video card.  Change it to whatever it is to vesa so it would look something like 
```

Driver                   "vesa"

```
Now, save it and exit by holding down <Ctrl> while hitting x.  Answer y when it asks if you want to save it with the same name.  Now, reboot and see if X will start.  If it does, then follow the this post to install nvidia driver for your video...

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by JanHammer on 2006-04-09
Will try, although I doubt it since it seemed the whole PC was locked up. Will reply with an EDIT.

EDIT: No, like I said it is completly locked up. And taurus how can there be a username and password if it's a live disc? O_o Plus I don't think it's even in the OS yet, just loading it all.

---

### Post by JanHammer on 2006-04-14
No one has any ideas? :/

---

### Post by JanHammer on 2006-04-17
Ok well it seems no one can help. But I just did a real install of it and I get the same problem, so it isn't the live CD.

---

