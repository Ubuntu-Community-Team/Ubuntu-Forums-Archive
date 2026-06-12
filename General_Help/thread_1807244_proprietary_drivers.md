---
title: "proprietary drivers"
date: 2011-07-18
forum: General Help
---

### Post by ajb359 on 2011-07-18
Hey,

I recently installed Ubuntu and was wondering why my graphics driver is activated but not 'currently in use'. I have a quadro 4000 and am running 11.04 Ubuntu on a Dell precision t3500 (64 bit).  The reason I am wondering is because when I try to activate the cube setting in compiz ubuntu crashes and I have to login Ubuntu classic to reset compiz and unity. Any help would be great!

Thanks,

---

### Post by Frogs Hair on 2011-07-18
For Unity 

Restart with the button on the computer , when the login screen comes up select your user name and enter the password . 

Before login , select the recovery console from the session list below the greeter box on the bottom panel.

Enter the following code and restart the computer ```
unity --reset
```
When login screen comes up again select Ubuntu from the session list .

See these  links. [http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

........[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

---

### Post by cwwilson721 on 2011-07-18
If nvidia-settings works, don't worry about it.

It is a well known nvidia/ubuntu issue. It IS working, just reporting that it is not.

Run 'nvidia-settings' in a terminal, and if it pops up, you're golden.

---

