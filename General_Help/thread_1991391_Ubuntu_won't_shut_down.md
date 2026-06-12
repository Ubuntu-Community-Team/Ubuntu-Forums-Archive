---
title: "Ubuntu won't shut down"
date: 2012-05-30
forum: General Help
---

### Post by Jedit Ojanen on 2012-05-30
I'm using Ubuntu 12.04 and every time I try to shut down my computer it just freezes and I have to force shut down it by pressing power button. This happens every time.

---

### Post by TM720 on 2012-05-30
Not an expert here, but does

sudo shutdown now

work?

---

### Post by Zvlwab on 2012-05-31
If you're using
```
sudo halt
```
You should instead use
```
sudo halt -p
```

---

### Post by 2sondad on 2012-06-02
> **Zvlwab said:**
> If you're using
```
sudo halt
```You should instead use
```
sudo halt -p
```

The command doesn't do anything.  The shutdown simply blanks the screen, but does not shutdown the power.

---

### Post by inashdeen on 2012-06-02
I would like to say up for the issue :)

---

### Post by linux653 on 2012-06-02
> **Zvlwab said:**
> If you're using
```
sudo halt
```You should instead use
```
sudo halt -p
```

That wouldn't work. Halting the system wouldn't turn off the power. It's the same thing as getting a BSOD or a Kernel Panic. Normally, Ubuntu when shutting down will tell you what is happening through a text based system. What does it say when you try to shut down your computer?

---

### Post by sammiev on 2012-06-02
On your next shutdown, press the down arrow right after you select shutdown.

---

### Post by 2sondad on 2012-06-02
> **linux653 said:**
> That wouldn't work. Halting the system wouldn't turn off the power. It's the same thing as getting a BSOD or a Kernel Panic. Normally, Ubuntu when shutting down will tell you what is happening through a text based system. What does it say when you try to shut down your computer?


I've also done it with *sudo shutdown -p  *and that did not work.  I have seen many people complaining about this bug, but it doesn't seem to be addressed.

Thank you for the assist, nonetheless.

---

### Post by 2sondad on 2012-06-02
> **sammiev said:**
> On your next shutdown, press the down arrow right after you select shutdown.


Now this worked!  I thank you!

---

### Post by sammiev on 2012-06-02
> **2sondad said:**
> Now this worked!  I thank you!

LOL I wanted to see the error that you would of received. It would of been displayed.

---

### Post by Jedit Ojanen on 2012-06-12
Thanks for the replies. Now this bug occurs just sometimes.. I think atm my computer shuts down just fine more regularly than doesn't shut down at all.

---

### Post by jsmanian on 2012-06-12
Hi,

   Sorry to disturbing this thread. I also faced same issue in my desktop. Please check this thread opened by me. 

 [http://ubuntuforums.org/showthread.php?t=1985849](http://ubuntuforums.org/showthread.php?t=1985849)

Till now I could not find any solution for this bug.

any comments?

with regards,
Subramanian

---

