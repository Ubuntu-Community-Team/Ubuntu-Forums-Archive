---
title: "Maverick 10.10 Firefox issues"
date: 2010-10-13
forum: General Help
---

### Post by FullMetalManiac on 2010-10-13
Hey, guys.  Just installed Maverick.  Runs B-E-A-utifully, btw.  Only one problem so far.  Firefox won't work.  If I click on the icon in the menu panel, it acts as though it's starting, and then won't start, like it crashes or something.  I'm using Chromium at the moment, but, I'd much rather have Firefox back.  Any suggestions on how to fix this?

---

### Post by CompyTheInsane on 2010-10-13
What output do you get in the console when you type 
```

firefox

```
in the terminal?

---

### Post by Valère Bonnet on 2010-10-14
Hello,
I had the same problem. In fact the .mozilla folder was the root's property.
So the solution was:
sudo chown  -R  yourname:yourname /home/yourname/.mozilla
Good luck

---

### Post by FullMetalManiac on 2010-10-15
> **compugeek32 said:**
> What output do you get in the console when you type 
```

firefox

```
in the terminal?

```
Bus error
```

---

### Post by FullMetalManiac on 2010-10-15
> **Valère Bonnet said:**
> Hello,
I had the same problem. In fact the .mozilla folder was the root's property.
So the solution was:
sudo chown  -R  yourname:yourname /home/yourname/.mozilla
Good luck

THanks for the tip.  Will try it and post back :)

Got this back:
```
chown: cannot access `/home/stephen/.mozilla': No such file or directory
```

lol  Maverick is starting to tick me off :p

---

