---
title: "Run GUI over SSH on HOST display"
date: 2011-07-12
forum: General Help
---

### Post by Jumbs on 2011-07-12
I use a lot of SSH, along with passing the X display to the client.

**I was wondering if I could open a program over the SSH terminal, but have the GUI pop up on the Servers screen.**

My goal is to combine this with the "nohup" command. 
Then i would be able to SSH in, open the program on my computer at home, then logout.

I have played around with the DISPLAY variable, but with no luck.

I assume this would be similar to when i have 2 monitors with separate X displays, but I have not been able to open one from another on that either.

---

### Post by nothingspecial on 2011-07-12
> **Jumbs said:**
> 

I have played around with the DISPLAY variable, but with no luck.



What did you try?
```

export DISPLAY=:0.0
```

The colon is necessary.

---

### Post by Jumbs on 2011-07-13
> **nothingspecial said:**
> What did you try?
```

export DISPLAY=:0.0
```

The colon is necessary.

Perfect.

I had done 
```

export DISPLAY=:0
```

as some site told me, but this one worked. I don't even think i need nohup, as it stayed open when i logged out.

---

### Post by nothingspecial on 2011-07-13
No problem. It's usually the colon that gets people. :rolleyes:

---

### Post by Jumbs on 2011-07-13
Good to know.

This is useful for both work, and mischievousness

---

