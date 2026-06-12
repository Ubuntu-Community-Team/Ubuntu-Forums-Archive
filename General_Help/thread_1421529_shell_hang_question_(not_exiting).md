---
title: "shell hang question (not exiting)"
date: 2010-03-04
forum: General Help
---

### Post by marbour on 2010-03-04
Hi.

Am new to shell... I have a script that contains the following line in it:
```
/home/dir/flashplayer /home/dir/file.swf
```The thing is that the shell executes the line and stays there... I need the rest of the shell script executed.

I tried nohup and screen... Both with the same result... The script stays there... waiting... and waiting... until I kill flashplayer.

I need this behavior changed. Can anyone help me?

Regards.

Marc

---

### Post by sisco311 on 2010-03-04
Launch the command in the background:
```
/home/dir/flashplayer /home/dir/file.swf **&**
```

See:
```
man bash | less +/Lists
```

---

