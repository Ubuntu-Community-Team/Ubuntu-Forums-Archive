---
title: "Opening File via SSH Also Opens New File"
date: 2012-07-02
forum: General Help
---

### Post by spartan21 on 2012-07-02
I am executing the following command to open a remote text file in gedit:

```
ssh -Y remote_machine 'gedit /home/user/Documents/file.txt'
```

The file opens in gedit, but another tab also opens in gedit with the filename "Untitled Document 1."  It seems as though the SSH command is simply not behaving as expected.  Is there something I can do so that only the file I want will open?

Thanks for your help!

---

### Post by papibe on 2012-07-02
Hi spartan21.

It looks like it is the same behaviour as this bug [here]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076").

It would be very helpful if you can confirm that, then add a comment to the bug so they can also knows it is happening over ssh.

Regards.

---

### Post by spartan21 on 2012-07-02
Thanks, I'll add the info.

---

