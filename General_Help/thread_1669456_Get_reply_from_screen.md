---
title: "Get reply from screen?"
date: 2011-01-17
forum: General Help
---

### Post by ThermalSloth on 2011-01-17
Hello,

First of all I'd like to let you know that I'm not very experienced with Linux,
and I am using Ubuntu 10.04.1 LTS

I'm also not really sure if this is the proper section in which I should post.
If it's not, then I apologize.


Now for my question.

I'm running a Minecraft server,
and I'm trying to make a PHP script grab the reply from a screen.
Is there any way to do this?

**Example**
You load "getnames.php" in /var/www/ and that file executes this command:
```
screen -x minecraft -X stuff "`printf "list\r"`"
```Now, in my screen "minecraft" this will return something like:
> 2011-01-17 22:32:28 [INFO] Connected players: name1, name2, name3Is there any way to grab the names "name1", "name2" and "name3"?
The amount of names can go up to 35 on my server.


I'd really appreciate any help I can get. :)

---

### Post by t0p on 2011-01-17
I don't play Minecraft, so I can't give you any specific info on command syntax; but I think **grep** is the command you need.  Grep searches input for patterns (eg character strings) that you specify, and prints the matching lines.

Check out the grep manpage for detailed info - open a terminal and type in the command

```

man grep

```

---

### Post by ThermalSloth on 2011-01-17
> **t0p said:**
> I don't play Minecraft, so I can't give you any specific info on command syntax; but I think **grep** is the command you need.  Grep searches input for patterns (eg character strings) that you specify, and prints the matching lines.

Check out the grep manpage for detailed info - open a terminal and type in the command

```

man grep

```
I can see how grep could work,
I just don't know how to properly use it..

I'll look into that, thanks. :)

---

