---
title: "Can't log in, Hard Disk full"
date: 2006-05-24
forum: General Help
---

### Post by graven on 2006-05-24
I was transferring movies from another hard drive to my Ubuntu drive when I appeared to reach the maximum, the copy files windows all gave an error message and froze. I decided to restart but when I get to the login page now, I always get the same thing, can't write to the *something something* and therefore can't login. One of the suggested reasons is that the disk if full. So anyway I have a two part question;

1) I think Window$ has a way of preventing you from over filling a disk, does Ubuntu have something similar - at least a warning? If so, how can I turn it on?

2) How can I free some space if I can't login? The live disk won't map the drive and I think that if Ubuntu is to go mainstream, this is the sort of thing I shouldn't need to know how to do. Is there a better way?

---

### Post by Craig Caldwell on 2006-05-24
you should still be able to boot into safe mode. Then you can delete to your hearts content.
don't delete  Deadwood, Firefly or The Office (english) because they never get old. ;)

---

### Post by graven on 2006-05-24
I am pretty sure I tried safe mode (98%), but I think it still didn't work. I am thinking it must be trying to log my login and can't, therefore I get the error. But will try again when I get home.

Never heard of Firefly, but Deadwood is great ain't it, ya c**ks**ker?

---

### Post by codejunkie on 2006-05-24
[QUOTE=graven]I am pretty sure I tried safe mode (98%), but I think it still didn't work. I am thinking it must be trying to log my login and can't, therefore I get the error. But will try again when I get home.

Never heard of Firefly, but Deadwood is great ain't it, ya c**ks**ker?[/QUOTE]
press ctrl+alt+F1 this will take you to a fullscreen terminal login there and enter ```
sudo apt-get clean
```this should give you around 500MB+ free space by cleaning the apt cache then hit ctrl+alt+F7 to get back to the login prompt and it should let you login.

---

### Post by graven on 2006-05-24
Sounds brilliant! WIll do that when I get home - thanks, codejunkie.

---

