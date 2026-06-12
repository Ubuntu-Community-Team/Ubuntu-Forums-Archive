---
title: "Clear contents of clipboard"
date: 2009-08-07
forum: General Help
---

### Post by Chamillionaire2 on 2009-08-07
What's Up?

OK, For my new project i need to be able to clear the contents of the clipboard via terminal. Is their away to do that?

Thanks Bye

---

### Post by Chamillionaire2 on 2009-08-07
[ ](www.google.co.uk)!

---

### Post by dli8ilb on 2010-11-18
sorry to bump an old one, but i was searching with the same question and ended up here.

install xclip:
> sudo apt-get install xclip

terminal command to clear the clipboard:
> echo -n | xclip -selection clipboard

credit to Jordan_U in #ubuntu for the solution.

---

### Post by WorMzy on 2010-11-18
```
xsel -bc
```
Will do it for the clipboard.

---

### Post by dli8ilb on 2010-11-18
thanks, WorMzy.  i was hoping for a way to clear it without having to install anything else.

---

