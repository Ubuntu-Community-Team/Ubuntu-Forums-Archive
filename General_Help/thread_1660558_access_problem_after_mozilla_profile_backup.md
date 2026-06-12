---
title: "access problem after mozilla profile backup"
date: 2011-01-05
forum: General Help
---

### Post by klirka on 2011-01-05
hello,

1) i have backed up my firefox and thunderbird profiles from my old kubuntu.
2) bought a new internal hard disk, installed kubuntu on it
3) copied the old fx and tb profiles into the respective new locations on /home/.mozilla and /home/.thunderbird and exchanged the appropriate filename in profiles.ini as well.

now i can open both programs, but i receive warnings.
when i want to open thunderbird, i receive the warning:

```
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.
```

when opening firefox, i receive the same warning 3x!

other issues:
in thunderbird, when i want to fetch my mail, i cannot. it tells me:
```
Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disk space to copy the mailbox.
```

in thunderbird, if i want to access "Account settings --> Local folders --> Junk settings", it says:
```
Unable to load address book file impab-1.mab. It may be read-only, or locked by another application. Please try again later.
```

also, thunderbird doesn't find my address books.

firefox recognizes all my bookmarks, but crashes repeatedly if i want to import a newer bookmarks.json.

there may well be one and the same root cause to all of this. my new big and empty hard disk can hardly be the problem. it might be a permission problem rather, but i checked the folder properties and did not find anything suspicious there; owner has read and write permission.

all this is a mozilla question rather than a ubuntu one, but since forum members are often so helpful here, i thought i try here. - any ideas? thanks for posting them!

---

### Post by klirka on 2011-01-05
errrrrrrrrh :(
my apologies!
the folder was in fact read/write, but all subfolders were not, so i think i fixed it now already myself.

---

