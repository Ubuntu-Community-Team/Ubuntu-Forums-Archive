---
title: "Shutdown and Restart hang on black screen..."
date: 2009-11-26
forum: General Help
---

### Post by Cytochromec on 2009-11-26
So whenever I try an shutdown or restart the white Ubuntu (9.10) logo shows, then it goes to a black screen, then it hangs for good. I have no idea how to go about fixing this one. Any help would be appreciated, thanks.

---

### Post by DougInKY on 2009-12-13
No replys on your post. I was hoping that someone might have an answer as I am having the same problem in 9.10. Never had this on any prior version of Ubuntu...

Doug in Kentucky

---

### Post by john newbuntu on 2009-12-14
Does hitting the escape key or Ctrl+alt+F2 take you to a terminal?
If you can get to a terminal, try and start gdm using the command:
sudo /etc/init.d/gdm start

If you can not, could you mount your root directory using a live cd and check on the kernel and syslogs to see if you have any errors?

---

