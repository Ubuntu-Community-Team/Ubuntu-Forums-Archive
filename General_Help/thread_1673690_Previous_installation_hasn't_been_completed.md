---
title: "Previous installation hasn't been completed"
date: 2011-01-22
forum: General Help
---

### Post by Zethioth on 2011-01-22
I recently installed Ubuntu on my laptop that has a bad batter. While installing Wine on it, I didn't notice my charging cable had become unplugged. My batter died while Wine was installing and now I can't re-install Wine or anything else.

My research showed to type[FONT=monospace]:
[/FONT]```
sudo dpkg --configure -a
```
into the terminal. When I do that. I get this:

```
dpkg: parse error, in file '/var/lib/dpkg/updates/0017' near line 0:
 newline in field name `#padding'
```Please help me. 

[FONT=monospace]
[/FONT]

---

### Post by Zethioth on 2011-01-23
Please help me someone. I am really interested in using Ubuntu/Linux but if this error leaves my Linux OS stuck, I might as well stick to Windows.

---

### Post by SeijiSensei on 2011-01-23
Try 
```
sudo apt-get install -f
```

This often fixes a partial or broken installation.

---

### Post by Zethioth on 2011-01-23
I typed that in, then entered my password. I was given this:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by Zethioth on 2011-01-23
Please help. I'm only bumping this thread so I can solve this problem.

---

