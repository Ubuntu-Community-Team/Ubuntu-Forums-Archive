---
title: "Bash Shell Script Question"
date: 2010-01-30
forum: General Help
---

### Post by vttay03 on 2010-01-30
--I'd like to modify an existing shutdown script that I currently have to look for a process and kill it before shutting down my computer.  Basically, I have conky running and I'd like to combine the following commands into one useful script

```

ps -ef | grep conky

```

If conky is running then,

```

pkill conky
shutdown -h now

```

Otherwise,

```

shutdown -h now

```

As you can see, I've got all the pieces besides that middle "If" portion.  Any ideas?

---

### Post by falconindy on 2010-01-30
```
#!/bin/sh
[ $(pgrep conky) ] && pkill conky
shutdown -h now
```

---

