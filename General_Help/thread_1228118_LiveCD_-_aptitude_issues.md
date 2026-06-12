---
title: "LiveCD - aptitude issues"
date: 2009-07-31
forum: General Help
---

### Post by Muscovy on 2009-07-31
I've been trying to customize a liveCD, but when I get to
```

dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -nr | less
aptitude purge package-name

```
it says I don't have permision. When I sudo or root the command, it runs the command on the filesystem. In other words, I can't change the CD's packages.
  What am I doing wrong?

---

### Post by cariboo on 2009-07-31
> **Muscovy said:**
> I've been trying to customize a liveCD, but when I get to
```

dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -nr | less
aptitude purge package-name

```
it says I don't have permision. When I sudo or root the command, it runs the command on the filesystem. In other words, I can't change the CD's packages.
  What am I doing wrong?

You need to add sudo to the command:

```
sudo dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -nr | less
aptitude purge package-name
```

---

### Post by Muscovy on 2009-07-31
Upon using, say purge gimp, done as 
```

sudo dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -nr | less
aptitude purge gimp

```
it will open a list of all packages (IDK if it's ~/live/edit or /), which is then closed. Nothing else.

---

