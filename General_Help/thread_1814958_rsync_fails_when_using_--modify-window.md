---
title: "rsync fails when using --modify-window"
date: 2011-07-30
forum: General Help
---

### Post by jocampo on 2011-07-30
I am trying to sync or copy some files from my local home directory to my external passport drive. My passport drive has been acting weird , I was having a hard time mounting it, but finally I did it. It was mounted using FAT (for compatibility reasons)

Now I am trying to copy the files but in a smart way, using this script with --modify-window switch


```

echo "iTunes Backup started at `date`"
rsync -rltDvu --modify-window=1 [source] [target] >/home/backup.log 2>&1
echo "Finished at `date`"

```

But it does nothing, not working

When running it manually, just the 1st part, it fails with this error:

```
Unknown filter rule: `y-window=1\#302\#240'
rsync error: syntax or usage error (code 1) at exclude.c(817) [client=3.0.7]
```

Is that a bug? Is the --modify-window switch missing on Ubuntu or maybe different?

---

### Post by papibe on 2011-07-31
I tested those options on my system. They work. A couple of questions:

Are you using bash?
Is that the exact script you are getting the error? because the characters [ ] are reserved on bash.

Once I got an error like that. I was using the -f and I forgot the put the filter in there, and rsync confused the next options as filters.

Regards.

---

### Post by jocampo on 2011-07-31
> **papibe said:**
> I tested those options on my system. They work. A couple of questions:

Are you using bash?
Is that the exact script you are getting the error? because the characters [ ] are reserved on bash.

Once I got an error like that. I was using the -f and I forgot the put the filter in there, and rsync confused the next options as filters.

Regards.

Thank you so much for reply! I do appreciate your help.

It was a really, really silly mistake (actually was not aware of that)

On the real script, the line with rsync, there was an additional space on the source file. I refused to accept that was the problem, but when I removed, it work. In other words, for some reason rsync on my machine was not working if immediately after the switch and before writing the source, an additional space was left; rsync for some reason was taking that as part of the file path and gives an error.

---

