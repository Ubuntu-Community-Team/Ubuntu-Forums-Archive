---
title: "unique id"
date: 2011-06-30
forum: General Help
---

### Post by jaes84 on 2011-06-30
How would i go about assigning a unique id to each time the script runs?
The reason i am asking is because i would like to make a new file whenever the script runs, but i need to keep the old one. For example:
```

First time i run the script, i want a file called:
001.foo
The second time, i want a file called:
002.foo

And so on...

```How can i make this happen?

EDIT: Never mind, i realized that would not be helpful to my script

---

### Post by arius13721 on 2011-06-30
I realize that you realized you don't need it, but the shell variable $$ is expanded to the process id.

So something in your script like 

```
echo "Test" > hello.$$
```

would produce a file name hello.21345 for example.

---

