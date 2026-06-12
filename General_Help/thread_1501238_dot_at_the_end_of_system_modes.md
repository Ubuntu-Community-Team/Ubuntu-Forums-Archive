---
title: "dot at the end of system modes?"
date: 2010-06-04
forum: General Help
---

### Post by Jungleboss on 2010-06-04
Simple question (I hope). What does the dot at the end mean?

drwxrwxr-x.

?

---

### Post by Jungleboss on 2010-06-04
I found it out by myself.
"it means the file has an access list with SELinux."

Although I don't understand how it got there. I have not set this myself.

---

### Post by bolucpap on 2010-06-04
SELinux access lists are not normally set or unset by users or admins anyway, AFAIK.

---

### Post by Jungleboss on 2010-06-04
My problems began with me not being able to access my mounted ext4 disk /media/archive. Then all files/directories disappeared from it. When trying to mount it I had to remove 'noatime' from fstab to get it to mount. noatime has always worked for me before! Then I saw that the selinux parameter was set. Don't know if that was initial problem or not. Really strange all of it. I wonder if I have a virus or something.

After removing noatime from fstab I now have it mounted alright.

---

