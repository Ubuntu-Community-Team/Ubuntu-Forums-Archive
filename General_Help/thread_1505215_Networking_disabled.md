---
title: "Networking disabled"
date: 2010-06-08
forum: General Help
---

### Post by jeffrey2009 on 2010-06-08
Intermittently after I reboot, I find that networking is disabled.  Not a big deal since I just right click and enable it, but just curios why this occurs.  I would also like to correct it.

Has anyone else experienced this?  Does anyone know how to fix it?

---

### Post by squenson on 2010-07-08
I have been facing the same issue since I upgraded to 10.04. At each reboot, the "Enable networking" option is not selected. As you said, not a big deal, but annoying.

---

### Post by NFblaze on 2010-07-09
Try
```

sudo nano /etc/network/interfaces

```

figure out which interface you need to add. Say, mine is eth0. So I add this line to make sure it's not disabled.
```

ifconfig eth0 up
```

---

### Post by Furry_Fighter_20x66 on 2010-07-09
I think I know this problem. It is the Network Manager doing stupid things. (Look, Trumpy, the network manager can do stupid things!) I have also had it lockup and refuse to allow me to re-enable it. Should this happen here is the steps to take:

In a shell, enter this command:
> sudo rm /var/lib/NetworkManager/NetworkManager.state

Then reboot. It will reset the Network Manager and all will be well with the world. Until it happens again. Fortunately, like most of you, it seems to only do it rather infrequently for me as well.

For you squenson, you might want to check your permissions on that file above. They should be 644 and owned by root. It might explain why it is acting up for you on every reboot.

---

### Post by squenson on 2010-07-10
Thank you Furry_Fighter_20x66 for the command, it seems to have solved the problem. The file had permissions set as -rw- r-- r-- which I think reads as 644, as you mentioned.

---

