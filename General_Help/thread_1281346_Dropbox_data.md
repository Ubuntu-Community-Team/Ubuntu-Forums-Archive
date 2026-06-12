---
title: "Dropbox data"
date: 2009-10-03
forum: General Help
---

### Post by spitfire23bc on 2009-10-03
Hi all, this may be completely obscure, but is there a way to access the percentage of Dropbox storage used, and the overall quota, without having to look at the notification area icon?

I'm writing a screenlet to display the current Dropbox status and would like to include this.

Thanks

---

### Post by akakingess on 2009-10-03
have you tried man dropbox and see if it gives you something in there?

---

### Post by spitfire23bc on 2009-10-03
> **akakingess said:**
> have you tried man dropbox and see if it gives you something in there?

Yes, I have. Currently there doesn't seem to be a 'dropbox --option' command to get the usage or quota, but I'm wondering if they are stored in a file somewhere.

---

### Post by Tibuda on 2009-10-03
You may use **du** to find out the size of your Dropbox folder, and then divide it by your total size. If you have 2 GB, try this:
```
expr 100 \* `du -s ~/Dropbox | grep '[0-9]\+' -o` / 2097152
```

This is far from the best solution, because the total quota is hardcoded, but at least your quota is not something you change everyday.

---

### Post by spitfire23bc on 2009-10-03
> **danielrmt said:**
> You may use **du** to find out the size of your Dropbox folder, and then divide it by your total size. If you have 2 GB, try this:
```
expr 100 \* `du -s ~/Dropbox | grep '[0-9]\+' -o` / 2097152
```

This is far from the best solution, because the total quota is hardcoded, but at least your quota is not something you change everyday.


Thanks danielrmt. I agree, it's not ideal, but it will do for now! I added the **-L** option to **du** to account for symlinks.

---

