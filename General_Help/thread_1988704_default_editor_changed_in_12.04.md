---
title: "default editor changed in 12.04"
date: 2012-05-28
forum: General Help
---

### Post by satish_j on 2012-05-28
I used 'sudo visudo' and it opened in nano instead of vi.
In lucid,it used to open in vi.
What setting needs to be done to open it in vi.
Thanks in advance.

---

### Post by maverickaddicted on 2012-05-28
Two ways to do that

**First Method**

This command will provide you the list of editors, and you can choose it from there -

```
sudo update-alternatives --config editor
```

**Second Method**

[http://ubuntuforums.org/showthread.php?t=779902](http://ubuntuforums.org/showthread.php?t=779902)
see ibuclaw post.
Just change the editor from gedit to vim.

---

### Post by Blackbird_13 on 2012-05-28
This worked for me ```
update-alternatives --config editor
```You should be presented with a choice of editors - select the one you prefer.

---

### Post by satish_j on 2012-05-30
> **maverickaddicted said:**
> 
This command will provide you the list of editors, and you can choose it from there -

```
sudo update-alternatives --config editor
```


Thanks,that did the trick..

---

