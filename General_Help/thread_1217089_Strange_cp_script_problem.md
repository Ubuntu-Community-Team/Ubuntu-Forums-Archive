---
title: "Strange cp script problem"
date: 2009-07-19
forum: General Help
---

### Post by Twizzle on 2009-07-19
I have a simple perl script, part of which copies folders to another folder but it is doing things I don't understand!

The line in question is:

$CP -al $DOCUMENTS $SNAPSHOT/daily.0;

which works and copies the contents of $DOCUMENTS into $SNAPSHOT/daily.0

Now, if I try:


$CP -al $DOCUMENTS $SNAPSHOT/daily.0/Documents;

I get an error - No such file or directory and low and behold, the folder daily.0 has gone!

I also tried:


$CP -al $DOCUMENTS $SNAPSHOT/daily.0;

$CP -al $PHOTOS $SNAPSHOT/daily.0;

which gives me /daily.0 containing the contents of $DOCUMENTS and then a subfolder /daily.0/Photos containing the contents of $PHOTOS.

All I really want is /daily.0 to contain two subfolders /daily.0/Documents and /daily.0/Photos and each of the subfolders to contain the corresponding contents of $DOCUMENTS and $PHOTOS

I even tried:


$CP -al $DOCUMENTS $PHOTOS $SNAPSHOT/daily.0;

but again, the /Daily.0 folder was removed!

I am very confused  :confused:

---

### Post by geirha on 2009-07-19
My best guess is that One of your variables contains pathnames with spaces or other special characters. Quote them to avoid the special characters being treated by the shell.

```
$CP -al "$DOCUMENTS" "$PHOTOS" "$SNAPSHOT/daily.0";
```

Also, "set -x" will turn on debugging in the shell. It should show you the command after the parameters have been expaneded. To turn off debugging again, run "set +x".

---

### Post by Twizzle on 2009-07-19
Thankyou

I realised that I had made two mistakes:

1. I had not read the script through properly and there was a small typo!
2. The script was renaming a folder earlier on and as a result it looked to me as if it was deleted....

I guess you learn from your mistakes and also loose a lot of hair!

---

