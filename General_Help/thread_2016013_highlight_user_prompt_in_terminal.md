---
title: "highlight user prompt in terminal"
date: 2012-07-04
forum: General Help
---

### Post by Ohzed on 2012-07-04
in the terminal, how do i change the color of, underline, or make bold somehow my userid@computername:~$ prompt so i can discern where is it more easily when alot of output is displayed in the terminal?

---

### Post by msammels on 2012-07-04
If you go to the preferences (hover over the top most bar and search for it), you can change the entire color scheme.

---

### Post by Ohzed on 2012-07-04
yeah i'm familiar with the terminal preferences, but it doesn't have an option where you can make the user@computername:~$ prompt section bold or anything.

---

### Post by msammels on 2012-07-04
That's... that's actually a good point. I wonder if someone else can present a .//hack for this.

---

### Post by nothingspecial on 2012-07-04
Hi have a look at this

[https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)

---

### Post by msammels on 2012-07-04
Ah, never saw this before, but not too sure how helpful it is - I think the OP was trying to make the prompt bold. Although, I could be wrong.

---

### Post by nothingspecial on 2012-07-04
To make it bold


```
export PS1="\[$(tput bold 1)\]\u@\h:\w $ \[$(tput sgr0)\]"
```

---

