---
title: "Things On Panel Always Move."
date: 2009-07-25
forum: General Help
---

### Post by TheNerdAL on 2009-07-25
Why Do the Things on my Panel Aways Move? Is There A way to Fix This?

---

### Post by wojox on 2009-07-25
?

---

### Post by wojox on 2009-07-25
Maybe right click and lock to panel maybe.

---

### Post by TheNerdAL on 2009-07-25
> **wojox said:**
> Maybe right click and lock to panel maybe.
Okay, but how can I move them?

---

### Post by Crunchy the Headcrab on 2009-07-25
Unlock them to move them and then lock them again to make them so they don't move anymore?  What exactly is the problem?  Things on my desktop don't really move even if they are unlocked unles I change my resolution or something.

Could you please provide more information or some screenshots of what is moving?

---

### Post by TheNerdAL on 2009-07-25
> **Crunchy the Headcrab said:**
> Unlock them to move them and then lock them again to make them so they don't move anymore?  What exactly is the problem?  Things on my desktop don't really move even if they are unlocked unles I change my resolution or something.

Could you please provide more information or some screenshots of what is moving?

The Icons.

---

### Post by kaibob on 2009-07-25
I don't know why icons on a panel would move about on their own. One thing you might try is to enable the following option in the configuration editor:

/apps/panel/global/locked_down

If that helps, you can use a small shell script to toggle this option on and off.

---

### Post by drs305 on 2009-07-25
Once you have them set where you want, you can save the setup to a file with the following command:
```

gconftool-2 --dump /apps/panel > ~/Desktop/panel.save

```
The example saves to the file "panel.save" on your Desktop but you can change both the filename and/or location.

To restore the panel to the saved condition:
```

gconftool-2 --load ~/Desktop/panel.save 

```

---

### Post by wojox on 2009-07-25
> **TheNerdAL said:**
> Okay, but how can I move them?

I thought they were already moving???

---

### Post by kaibob on 2009-07-25
> **drs305 said:**
> Once you have them set where you want, you can save the setup to a file with the following command:...
Thanks drs305. I've spent a lot of time getting my panels just as I like them, and it's nice to have a backup.

---

### Post by expatCM on 2009-07-25
I have also seen this behaviour.  It appears to be totally random, the panel icons stay as you want it day after day and then all of a sudden .... wham ...  the order is all messed up.

Lock to Panel seems to lock the item to the panel but it does not influence the order on the panel.

I have seen one thing that appears to be related and also not explained.....   Sometimes skype gets trashed.  It is necessary to complete the login manually and also change all the skype settings back to how you had them.  This happens from time to time ...  no cause seen ...  but the icon also sits on the panel ...

---

### Post by kaibob on 2009-07-26
This is a bug report that may be pertinent. I'm not sure if it is related to the OP's issue, as this bug appears to occur when changing screen resolution. This bug report was started in 2006 but has entries that continue to July 2009.

[https://bugs.launchpad.net/ubuntu/hardy/+source/gnome-panel/+bug/44082](https://bugs.launchpad.net/ubuntu/hardy/+source/gnome-panel/+bug/44082)

---

### Post by TheNerdAL on 2009-07-26
I got it, I think. :P

---

### Post by expatCM on 2009-07-26
the bug report makes a very similar description ....

---

