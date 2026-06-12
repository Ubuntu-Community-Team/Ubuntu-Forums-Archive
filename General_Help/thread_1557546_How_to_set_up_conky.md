---
title: "How to set up conky?"
date: 2010-08-20
forum: General Help
---

### Post by dukehunter1 on 2010-08-20
I've searched the forums a little bit and I'm having problems finding help with getting a .conkyrc file set up.  I've found the script I want for it but I have no idea what to do with it.  Most posts just say to put it in my home directory but that's a little bit to general for me.  Can anybody give me a little more specific directions?

---

### Post by ScarletWyvern on 2010-08-20
What exactly are you trying to do?

Your .conkyrc file just goes in your home directory.

/home/<your name>/.conkyrc or ~/.conkyrc

If you're talking about an actual script like a mail script or a weather script you want to run in conky, you're going to have to be more specific.

---

### Post by dukehunter1 on 2010-08-20
I found a link to script for a specific "themed" conky that I want to use.  Do I just create a file named .conkyrc and put it in my home directory?

---

### Post by ScarletWyvern on 2010-08-20
You literally name the text file of the conky set up ".conkyrc" and drop it in your home folder.

You're trying to make it more complex than it is. ;p

---

### Post by dukehunter1 on 2010-08-20
I have a habit of that.  So how do I run it after that?

---

### Post by ScarletWyvern on 2010-08-20
You just run conky from the command line.

```
conky
```

It'll automatically use the .conkyrc from your home folder as the configuration file.

Or, run it as a background process.

```
conky &
```

Then hit ctrl+c and close the terminal window. Of course, if you want you can just add it as a start-up program, too.

---

### Post by dukehunter1 on 2010-08-20
Works.  Thanks a ton.

---

