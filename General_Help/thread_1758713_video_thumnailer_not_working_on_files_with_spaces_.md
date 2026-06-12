---
title: "video thumnailer not working on files with spaces in their names??"
date: 2011-05-15
forum: General Help
---

### Post by ambdeep on 2011-05-15
Like the title says, ffmpegthumbnailer is not working on files with spaces in their names. If i rename the file with no spaces then it creates a thumbnail with no problem. Please help.

---

### Post by lmarmisa on 2011-05-15
Sorry I do not know ffmpegthumbnailer. Do you call that program from a terminal?.

```

ffmpegthumbnailer file1

```

If so, type the name of the file with spaces in its name between single quotes:

```

ffmpegthumbnailer 'file with spaces'

```

---

### Post by ambdeep on 2011-05-15
I tried as you suggested. When i sent the file in '' it worked, but without it i get the following error:
```
ffmpegthumbnailer -i /media/sdb1/Movies/3 10 To Yuma.mkv  -o test_thumbnail.png
Error: Could not open input file: /media/sdb1/Movies/3

```
I looked up the error on the net and they asked me to run the following command:
```
gconftool --all-dirs /desktop/gnome/thumbnailers | grep video | xargs -I DIR gconftool --set DIR/command --type string "/usr/bin/ffmpegthumbnailer -s %s -i %i -o %o -c png -f"

```
but it is now working. Is there any way of making nautilus send the name of the file in singe quotes?

---

### Post by lmarmisa on 2011-05-15
If you do not add quotes to the file name the program supposes you are passing several files as arguments. But these files do not exist (Error: Could not open input file: /media/sdb1/Movies/3).

In relation with your Nautilus question, I can not give you any answer.

Best regards,

Luis

---

### Post by ambdeep on 2011-05-15
Ive also tried passing %u instead of %i but it still makes no difference.

---

