---
title: "Piping etc. outside of terminals"
date: 2010-07-21
forum: General Help
---

### Post by Zorgoth on 2010-07-21
I have noticed that things like piping and such don't work in Alt-F2;
as an example, how would you achieve the same effect as:

echo "get -P /path/to/my/remote/file /path/to/local/destination" | sftp me@remote_computer

without, for example, a keyboard shortcut or launcher?

Well, in this case I need a password, so not such a good example...

---

### Post by Zorgoth on 2010-07-26
bash -c "command1 | command2" will do it

---

