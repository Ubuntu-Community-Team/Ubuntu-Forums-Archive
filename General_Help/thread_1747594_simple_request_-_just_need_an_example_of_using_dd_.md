---
title: "simple request - just need an example of using dd to copy a single file"
date: 2011-05-02
forum: General Help
---

### Post by Keypel on 2011-05-02
This should be an easy question for anyone that knows their way around a CLI.

ok, I have a really big file to transfer. I'm guessing it would be unwise to drag and drop in nautilus.

I'm also guessing I should use something low level like dd.

can somebody please give me an example of using dd to copy a single file from one directory on one hdd to another directory on another hdd?

I tried google'ing on dd but didn't understand a thing. 

I seem to understand better from looking at real examples. I should be smart enough to change the user name and path in your example.

---

### Post by nothingspecial on 2011-05-02
```
dd if=path_to_file_you_want_to_copy of=path_to_where_you_want_the_copy
```

---

### Post by Keypel on 2011-05-02
I tried to copy a test file on my desktop but something went wrong

```
ubuntu-01@PC-01:~$ dd if=~/Desktop new file of=/media/d912ddb5-7d07-4508-8b69-f94e807d90d0
dd: unrecognized operand `new'
Try `dd --help' for more information.
user-01@PC-01:~$
```

---

### Post by nothingspecial on 2011-05-02
You need to escape the spaces and specify a new file name

```
dd if=~/Desktop/new\ file of=/media/d912ddb5-7d07-4508-8b69-f94e807d90d0/new\ file.bak
```

I'd use cp

---

### Post by nothingspecial on 2011-05-02
Thinking about it

[COLOR="Red"][SIZE="2"]DEFINITLEY USE CP, YOU STAND A GOOD CHANCE OF WIPING YOUR EXTERNAL DRIVE[/SIZE][/COLOR]

---

### Post by Keypel on 2011-05-02
> **nothingspecial said:**
> Thinking about it

[COLOR="Red"][SIZE="2"]DEFINITLEY USE CP, YOU STAND A GOOD CHANCE OF WIPING YOUR EXTERNAL DRIVE[/SIZE][/COLOR]

the file is huge, about 36 hours to transfer. That's why I was thinking something low level like dd. Do you still think I should use cp instead?

---

### Post by nothingspecial on 2011-05-02
Use whatever you like, I have no idea how cp will handle a file that big.

What I do know is that if you get dd wrong you will wipe your external drive. So, like my sig says, make sure you know exactly what you are doing with dd before you do it.

---

### Post by Keypel on 2011-05-02
> **nothingspecial said:**
> Use whatever you like, I have no idea how cp will handle a file that big.

What I do know is that if you get dd wrong you will wipe your external drive. So, like my sig says, make sure you know exactly what you are doing with dd before you do it.

funny you mention wiping out a hdd because that's exactly what happened earlier today. I tried installing micro$ucks windbloz on an empty partition I had but, winbloz had no respect and decided to formate and write crap to both partitions. Lucky I keep a backup on a spare hdd.

I will mark this as solved, I have practiced with a test file a few times and this "should" work. I think dd has some cluster size options but since I don't know how to use them, I'll just go with this and keep my fingers crossed.

---

### Post by JKyleOKC on 2011-05-02
> **Keypel said:**
> the file is huge, about 36 hours to transfer. That's why I was thinking something low level like dd. Do you still think I should use cp instead?You say "huge" but how big is it, in MB or GB? I've copied files as large as 30 GB across my network from one machine to another, using "cp", in well under an hour. If you're copying from one directory to another on the same machine, it should go faster than that! Your time of 36 hours sounds like it might have been a download, which is always much slower than a local transfer...

---

### Post by Keypel on 2011-05-02
> **JKyleOKC said:**
> You say "huge" but how big is it, in MB or GB? I've copied files as large as 30 GB across my network from one machine to another, using "cp", in well under an hour. If you're copying from one directory to another on the same machine, it should go faster than that! Your time of 36 hours sounds like it might have been a download, which is always much slower than a local transfer...

huge as in TB.

It's dd'ing, I think everything will be fine.

---

