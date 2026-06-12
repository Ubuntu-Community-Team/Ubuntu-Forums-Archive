---
title: "How to move files into bin folder?"
date: 2010-05-31
forum: General Help
---

### Post by elidoperezmd on 2010-05-31
Thanks for the help guys...im trying to move a pytho script to the bin folder...but simply cant...i think is a permission problem or folder is protected. how to do it?

---

### Post by WinRiddance on 2010-05-31
If you want to have administrative privileges to do something that you ordinarily wouldn't be expected to do, you'll have to set yourself up accordingly. Just for the sake of discussion let's assume that there's a folder entitled majorbin which contains files that you want to move or copy to another folder entitled minorbin. Now let's assume that you have full access privileges to move stuff around or even out of majorbin, yet can't accomplish this because the other folder, minorbin, won't permit you to do that ...
... then you'll find relief by opening your terminal and entering this:

```
sudo chown -R yourusername:yourusername /fullpath/tofolderyouwant
```If your username was dude and the path to minor bin one like this: /media/minorbin
Then the command would look like this for you:

```
sudo chown -R dude:dude /media/minorbin
```**On a side note:**  One of the things that makes Linux so robust is that certain folders which should NEVER be accessed for any reason are being kept away from us on purpose. If you begin mucking around with such folders, in particular if they contain system sensitive files, **you take a chance on making your system unusable ....**

If you don't have administrative privileges on either of those folders then you'd need to use that command twice, once for each folder.

---

### Post by amite on 2010-05-31
To move ur file into /bin directory use sudo with mv command.............but it would lead u to use always sudo to run ur script.To avoid this u may use suggestion of[URL="http://ubuntuforums.org/member.php?u=1083274"] winriddance.
[/URL]

---

### Post by nothingspecial on 2010-05-31
Don`t change the ownership of /bin, that way ruin lies.

Move it with sudo.

Change myscript.sh to whatever your script is named.

```

sudo mv myscript.py /bin
```

---

### Post by elidoperezmd on 2010-06-03
i got it...ran gksu nautilus in the terminal... and that gives me permission...moved the file and closed it....

thanks for ur help and time

---

