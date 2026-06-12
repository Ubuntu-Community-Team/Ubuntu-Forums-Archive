---
title: "File/Folder Naming Differences Ubuntu/Windows"
date: 2010-06-22
forum: General Help
---

### Post by skooter1121 on 2010-06-22
All;

I am proposing to a small law firm, to switch from Windows to Ubuntu. I have previously set up some folder names such as: /! CLIENTS MAIN ! to be the TOP TOP Folder for storage, with the client name / ! CLIENTS MAIN !/# SMITH, JOHN # as TOP SECOND, with various subs underneath So they could easily identify where they saving files, and windows in an alpha sort always places ! named files/folders at the top.

Well, Ubuntu, sorts differently.

1. Is there a listing of the sorting method of Ubuntu? (As I have not been able to find a comprehensive one.)
2. Are there any other fundamental differences? 
    (like: Ubuntu considers A.txt a different file than a.txt, where windows considers them the same file)
3. Whats up with all those extra: periods, hyphens, and underscores in filenames? (Spaces in filenames are so much easier to read, and Ubuntu supports spaces)


Any other thoughts on Windows/Ubuntu idiosyncrasies?

-SK

---

### Post by -humanaut- on 2010-06-22
Here's a way to sort

find /home -size +2000k -ls | sort -n | grep gb > gig.txt

to learn more about sorting try man sort & man grep

---

### Post by Smart Viking on 2010-06-22
> **skooter1121 said:**
> All;
3. Whats up with all those extra: periods, hyphens, and underscores in filenames? (Spaces in filenames are so much easier to read, and Ubuntu supports spaces)


Spaces is filenames can cause trouble. Per example, if there is a file called "hi there"

```
smartviking@smartviking-desktop:~$ ls
hi there
smartviking@smartviking-desktop:~$ rm hi there
rm: cannot remove `hi': No such file or directory
rm: cannot remove `there': No such file or directory
smartviking@smartviking-desktop:~$ rm "hi there"
smartviking@smartviking-desktop:~$ ls -a
.
..

```If you know what i mean, they make things harder. :)

---

### Post by skooter1121 on 2010-06-22
Thanx Smart Viking for the commentary.

Yes, I understand the command line does make difficulties, as your example reflects. But, I could also use Nautilus to do the same things, and not worry about those spaces. And I believe that most commands have options that will permit you to do the same with allowing for spaces. 

So I still don't really need the need for the extra stuff. 

-SK

---

