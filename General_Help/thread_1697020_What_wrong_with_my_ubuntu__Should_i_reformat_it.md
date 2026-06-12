---
title: "What wrong with my ubuntu ? Should i reformat it ?"
date: 2011-02-28
forum: General Help
---

### Post by crownclown on 2011-02-28
I dont what wrong with my ubuntu..
i want to install by typing command also cannot , it goes the same error..
or should i reformat it ?  or there have any solution of it ?
every time it goes like this , when i want to install anything.
can somebody help me with it...
even i type : sudo apt-get install update  also cant... 
sorry if my english is not good....



[IMG]http://i377.photobucket.com/albums/oo218/noob_crown/Screenshot-3.png[/IMG]

---

### Post by Grenage on 2011-02-28
You're not using Lucid, I presume?  Under *Update Manager*, click *Settings* and then*Other Software*.  Untick anything mentioning Lucid, then try again.

---

### Post by marin123 on 2011-02-28
```
sudo apt-get update
```

what does that return?

i think you messed up the keys.

is your internet connection working? can you access the web?

---

### Post by frotzed on 2011-02-28
> **Grenage said:**
> You're not using Lucid, I presume?

He is definitely using Lucid (cf. Wallpaper and window buttons).

@OP: Is this problem still happening?  My first guess is that there was a temporary connectivity issue.

---

### Post by Grenage on 2011-02-28
> **frotzed said:**
> He is definitely using Lucid (cf. Wallpaper and window buttons)

Cheers for the catch; the default look lasts about 3 minutes on my machines, so I can never identify a base install.

In which case, I would also assume connectivity is the issue; either name resolution or a complete lack of it.

---

### Post by frotzed on 2011-02-28
> **Grenage said:**
> Cheers for the catch; the default look lasts about 3 minutes on my machines, so I can never identify a base install.

Completely understandable.  I'd have missed it too if I didn't just install 10.04 on my home file server yesterday ;)

---

### Post by crownclown on 2011-03-01
well i try it to unclick the lucid things at other software..and restart..and it success .... thx man...thx guys for helping me...

---

### Post by Grenage on 2011-03-02
Hi there,

Since you are apparently using Lucid, you're probably going to want those repositories selected, so that you can get updates and the like.

I would reselect them, then post the output of:

```
cat /etc/apt/sources.list
```

You'll need to type that into a terminal, or you could alternatively open it in gedit.

---

