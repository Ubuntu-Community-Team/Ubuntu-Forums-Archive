---
title: "Check GMail icon in Lucid"
date: 2010-06-29
forum: General Help
---

### Post by andypi on 2010-06-29
Since upgrading to Lucid, the "Check GMail" icon in the system tray doesn't fit in to the Lucid colour scheme (see screenshot).

The preferences offer a "Set Tray Background" option, but this doesn't seem to make a difference. Anyone had this problem and managed to sort it out?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=161929&stc=1&d=1277853368[/IMG]

---

### Post by tom.swartz07 on 2010-06-29
Yup yup, theres a fix.

Open the terminal (Applications, accessories, terminal)
and type the following command into the window.

```
sudo checkgmail --update
```

I noticed that problem about a month ago, and they had already pushed the update.

---

### Post by andypi on 2010-06-30
Thanks!

---

### Post by tom.swartz07 on 2010-06-30
> **andypi said:**
> Thanks!

Sure! Dont forget to mark the thread as solved from the thread tools at the top

---

### Post by Rolandmaffia on 2010-08-23
> **tom.swartz07 said:**
> ```
sudo checkgmail --update
```
I've got same problem, but the update isn't solved it.
> 
$ uname -r
2.6.32-24-generic-pae
$ checkgmail -h
CheckGmail v1.14pre-svn Copyright © 2005-10 Owen Marshall
$ apt-cache policy compiz
compiz: Installed: 1:0.8.4-0ubuntu15
$ apt-cache policy avant-window-navigator
avant-window-navigator: Installed: 0.4.0-0ubuntu1

What can I do?!

---

### Post by amirhomayoun on 2010-08-26
> **Rolandmaffia said:**
> I've got same problem, but the update isn't solved it.

What can I do?!

Same problem here. Have tried everything, no luck!

---

### Post by ferossan on 2010-08-26
> **amirhomayoun said:**
> Same problem here. Have tried everything, no luck!

In Lucid, it only works with Ambiance default theme.

---

### Post by Stefanie on 2010-08-26
I modified the latest svn version to fix this problem for other themes than Ambiance. Transparency doesn't work, but now you can change the background to whatever color you want. 

You can download the file here: [http://dl.dropbox.com/u/555601/checkgmail](http://dl.dropbox.com/u/555601/checkgmail)

Save the file to your home folder, then open a terminal and copy it to /usr/bin

```

sudo cp checkgmail /usr/bin

```

and make it executable 
```

sudo chmod +x /usr/bin/checkgmail

```

Restart checkgmail, set the tray background, and restart again.

---

### Post by pantherattack on 2010-09-15
One thing that foiled me for a while: the --update asks you a <Y/n> question about whether to proceed. Just pressing ENTER doesn't work, you need to type a capital Y and then ENTER.

---

### Post by synergie on 2010-10-23
> **Stefanie said:**
> I modified the latest svn version to fix this problem for other themes than Ambiance. Transparency doesn't work, but now you can change the background to whatever color you want. 

You can download the file here: [http://dl.dropbox.com/u/555601/checkgmail](http://dl.dropbox.com/u/555601/checkgmail)

Save the file to your home folder, then open a terminal and copy it to /usr/bin

```

sudo cp checkgmail /usr/bin

```and make it executable 
```

sudo chmod +x /usr/bin/checkgmail

```Restart checkgmail, set the tray background, and restart again.

Very nice work!!!! Worked perfectly, thanks

---

### Post by orang_letrik on 2011-01-12
wow! it worked. thanks a lot =)

---

### Post by Elitist on 2012-03-06
Thank you a lot! The change in code worked like a charm!

:popcorn:

---

### Post by Rytron on 2012-09-30
Is it possible to make the checkgmail icon have a transparent background?

---

### Post by overdrank on 2012-09-30
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

