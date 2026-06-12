---
title: "terminal - ls colours have gone"
date: 2011-03-26
forum: General Help
---

### Post by burton247 on 2011-03-26
If I type ls into the terminal it used to colour the name differently but now it doesn't. It behaves the same as dir.

I have been playing around with the profile settings to change some colours and transparency etc for the purposes of VIM.

I can't seem to get it back though, does anyone know how to do this? A Google search showed up nothing.

Cheers

---

### Post by AlphaLexman on 2011-03-26
What do you get from```
ls --color=auto
```Maybe you lost an alias.

---

### Post by burton247 on 2011-03-26
That still doesn't give me my colours back :( nor does color=always

---

### Post by Spyderkid on 2011-03-26
try *ls -l* instead it should work

or try  *dir* ('dir' is meant to be the non-coloured one, but they might have sqitched around somehow)

---

### Post by AlphaLexman on 2011-03-26
Umm, interesting...

Do you have a color prompt?
Does 'grep --color=auto' work?

Can you 'echo' a color sequence?```
echo -e "\e[1;31m Text"
```

---

### Post by Krytarik on 2011-03-26
To restore the defaults, copy the content of "/etc/skel" into your home directory.

Greetings.

---

### Post by AlphaLexman on 2011-03-26
> **Krytarik said:**
> To restore the defaults, copy the content of "/etc/skel" into your home directory.
Make backups first!

---

### Post by burton247 on 2011-03-26
Made a backup, and changed to those in skel and everything is back to working again, thanks.

Just for the record I didn't get grep thing to work, running echo -e "\e[1;31m Text" changed the colour of "Text" and changed the font colour for all my terminal. Finally, ls -l did not colour anything.

Working now though, thanks again

---

### Post by AlphaLexman on 2011-03-26
I'm sorry, I didn't reset the [COLOR="Red"]red[/COLOR] I gave you, here is the correction:
```
echo -e "\e[1;31m Text\e[0m"
```

---

### Post by Krytarik on 2011-03-26
> **AlphaLexman said:**
> I'm sorry, I didn't reset the [COLOR=Red]red[/COLOR] I gave you, here is the correction:
```
echo -e "\e[1;31m Text\e[0m"
```
I noticed that. :D I also tried that code, just for fun.
I just re-opened the terminal then.

---

### Post by burton247 on 2011-03-26
> **AlphaLexman said:**
> I'm sorry, I didn't reset the [COLOR="Red"]red[/COLOR] I gave you, here is the correction:
```
echo -e "\e[1;31m Text\e[0m"
```

Haha, that's fine

---

