---
title: "Problem installing Picasa"
date: 2010-01-24
forum: General Help
---

### Post by alan_uk on 2010-01-24
I installed Picasa. When I click on it I get the following error:
/dev/nvidia0 or /dev/nvidiact1 are not accessible. Picasa will crash if these files are accessible. To fix this, as root,please run:
chmod 666 /dev/nvidia0 /dev/nvidiact1

so I did....and I get:
chmod: changing permissions of `/dev/nvidia0': Operation not permitted
chmod: cannot access `/dev/nvidiact1': No such file or directory

Is there something wrong with the input instructions or I am I missing something else?

Thank you

Alan

---

### Post by s.fox on 2010-01-24
Hello,

I found [this]("http://ubuntuforums.org/showthread.php?t=1071915") thread describing the same problem.  Perhaps the solution will also work for you.

-Silver Fox

---

