---
title: "wastebasket contents not showing"
date: 2009-09-12
forum: General Help
---

### Post by amx109 on 2009-09-12
when i click the wastebasket icon, a window loads, the gnome 'spinner' appears (mouse icon, and for top-right folder icon) but no contents are shown

ive checked the .Trash directories and they have stuff in there.

can anyone help? why am i not seeing the contents?

---

### Post by amx109 on 2009-10-10
fixed it. there was an 'invalid coding' filename. ie it used a special character that the system couldnt handle. once i removed the invalid character and the '(invalid coding) text from the filename, the wastebasket started to show its contents again.

note, each filesystem has a .Trash-xxx folder where the trash'd files can be located

---

### Post by drs305 on 2009-10-10
> **amx109 said:**
> fixed it. there was an 'invalid coding' filename. ie it used a special character that the system couldnt handle. once i removed the invalid character and the '(invalid coding) text from the filename, the wastebasket started to show its contents again.

note, each filesystem has a .Trash-xxx folder where the trash'd files can be located

I wrote a post about Trash a while ago (link in signature line) and would like to add a note about this. Can you give me an example of the filename?

My understanding is that you couldn't empty the wastebasket or see the contents. You then manually looked into the trash bin with a file browswer, found an oddly-named file, deleted it and then the Wastebasket started working? 

Thanks.



*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

