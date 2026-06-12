---
title: "Get latest file via FTP command line"
date: 2011-02-10
forum: General Help
---

### Post by CrusaderAD on 2011-02-10
How can I make a shell script that downloads the latest file via ftp? I've tried a few things but I get invalid commands. I know ftp commands are limited, but does anyone have an idea?

---

### Post by Habitual on 2011-02-10
define "latest"?

---

### Post by Habitual on 2011-02-10
define "latest"?

What have you tried exactly?

---

### Post by Cheesehead on 2011-02-10
Use wget or curl.

---

### Post by CrusaderAD on 2011-02-10
Latest. As in the file with the most recent time stamp. I tried this in a shell script:

```

ftp -n ADDRESS <<!
quote user USERNAME
quote pass PASSWORD
cd /
FILE=$(ls -rt | awk 'END{ print $NF }')
lcd /home/user/ftp
get $FILE
quit

```

---

### Post by CrusaderAD on 2011-02-10
Hey Cheesehead, with wget, can I get the latest file without knowing the exact file name? The problem is that the file name changes.

---

### Post by Cheesehead on 2011-02-10
Use it twice. First to get the list of files.
```
If you specify a directory, Wget will retrieve the directory listing, parse it and convert it to HTML. Try:
wget ftp://prep.ai.mit.edu/pub/gnu/

Or your can -O output it some other way...like stdout instead of a saved file.
wget -O - ftp://prep.ai.mit.edu/pub/gnu/

Or you can -S to spider it and avoid all the HTML output
(It will create an HTML output anyway, so let's send that to /dev/null)
wget -O /dev/null -S ftp://prep.ai.mit.edu/pub/gnu/

And set directory-depth to 1 so it just pulls the directory list I asked for.
wget -O /dev/null -S -l 1 ftp://prep.ai.mit.edu/pub/gnu/

```

Then do your logic to figure out which file is newest. (Look, the output is in columns already! Hooray for 'sort -k' and 'grep'!

Then wget a second time to actually get the file you want.

---

### Post by CrusaderAD on 2011-02-11
wget isn't working. Might be some kind of restrictions on the server... need to stick with an ftp shell script. Any other ideas?

---

### Post by Cheesehead on 2011-02-11
Try the --verbose flag to see what the problem is...
Don't forget man wget to learn about a lot of the features (like login) that I haven't even touched.

---

### Post by CrusaderAD on 2011-02-11
It resolves the host but can't connect. I've used wget many times before, but usually on servers I have full access to. I was thinking... is there a way to "download all" via an ftp shell script? I mean, how do people do it when they don't know the exact file name and need to get the latest file? Like is the file is testfileMMDDYYYY.txt. I see this being a common occurrence and I can't believe I haven't found a solution yet... strange.

---

### Post by CrusaderAD on 2011-02-11
I think I've got a quick fix for this. I FTPed all files with:

```

prompt
mget *

```

prompt gets rid of the y/n prompt you get. From here I can run scripts to get the latest file and rename it on the local machine without doing it via FTP. I can do this cause the files aren't very big but I can see this becoming a problem if things get too large. Any other ideas are welcome. Thanks!

---

