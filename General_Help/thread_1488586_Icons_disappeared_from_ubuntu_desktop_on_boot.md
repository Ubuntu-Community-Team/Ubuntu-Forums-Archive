---
title: "Icons disappeared from ubuntu desktop on boot"
date: 2010-05-20
forum: General Help
---

### Post by Dejavou42 on 2010-05-20
I recently had a problem that was bugging me for several days. I figured that I should probably make a post on it in case anyone else ran across the same problem. 

My gnome desktop was not showing up after reboot, and everytime I booted, I had to kill nautilus to get it to come back. 

```

killall nautilus

```

After looking around for a while, I found this post: [http://www.linuxquestions.org/questions/linux-software-2/gnome-icons-disappeared-73536/]("http://www.linuxquestions.org/questions/linux-software-2/gnome-icons-disappeared-73536/"). Basically, I deleted my .gnome2 folder in my home folder. Apparently something was broken there, and it was recreated on the next boot.

Hope this helps someone!

---

### Post by ubunterooster on 2010-05-20
I sometimes have same problem with xfce, thanks.

---

