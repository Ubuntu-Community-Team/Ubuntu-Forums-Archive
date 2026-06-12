---
title: "Delete the previous commands"
date: 2012-01-23
forum: General Help
---

### Post by community on 2012-01-23
Can anyone tell me the command to display the previously executed terminal commands and the command to delete all of them???

---

### Post by nothingspecial on 2012-01-23
You can't delete them but hopefully you can reverse them. To see them type

```
history
```

---

### Post by community on 2012-01-23
What do you mean by reversing it?

---

### Post by Cheesemill on 2012-01-23
To display previous commands you can use the up arrow or for a complete list type:
```
history
```

To remove this history just delete ~/.bash_history

---

### Post by Paqman on 2012-01-23
> **nothingspecial said:**
> You can't delete them

Well you can't undo them automatically, but you can clear the history:
```
history -c
```

---

