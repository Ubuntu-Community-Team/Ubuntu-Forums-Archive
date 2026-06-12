---
title: "Unable to Unmount the filesystem"
date: 2011-07-02
forum: General Help
---

### Post by Siva Sankaran on 2011-07-02
I have used the command "umount -v /media/label1". But I can't unmount. The command gives message that "umount: /media/label1 is not in the fstab (and you are not root)"
  In places menu it shows the label1 two times.one is working and another one is not working


   How can I Unmount this?

---

### Post by wildmanne39 on 2011-07-02
> **Siva Sankaran said:**
> I have used the command "umount -v /media/label1". But I can't unmount. The command gives message that "umount: /media/label1 is not in the fstab (and you are not root)"
  In places menu it shows the label1 two times.one is working and another one is not working


   How can I Unmount this?Hi, try sudo before the command to give you root, you will have to enter your password.

---

### Post by Siva Sankaran on 2011-07-02
When I open the GParted Partition Editor after mounting a file system, the label of the file system appeasrs twice in places menu.
Why this happens.

    In this scenario only the above Unmounting problem arises.If I am not opening Gparted partition editor, unmounting is normal.why ?

  Another thing which I can't understand is the filesystem which can't be unmounted(which appears twice in places menu) can be unmounted using Gparted Partition editor.

  And I am sure that the file system is not in use when I am trying to unmount using command "umount -v /media/label1"

---

### Post by Siva Sankaran on 2011-07-02
> **wildmanne39 said:**
> Hi, try sudo before the command to give you root, you will have to enter your password.

 thank you it works. I can unmount it. Why this happens

---

### Post by wildmanne39 on 2011-07-02
> **Siva Sankaran said:**
> thank you it works. I can unmount it. Why this happensHi, I am not sure, but I am glad it worked, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

