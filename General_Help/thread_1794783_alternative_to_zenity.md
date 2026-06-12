---
title: "alternative to zenity?"
date: 2011-07-01
forum: General Help
---

### Post by LuniTux on 2011-07-01
Hello,

I am writing a script that requires the user to select a file. The script works correctly but zenity seems to have problems. If I have to scroll to select a file, a file different than the one I selected appears.

```
filename=`zenity --file-selection --title "Select A File to Encrypt"`
echo "$filename"
```

I was wondering if there was an alternative to zenity that can do the same thing. I would prefer a terminal based program if possible.

Thanks,

---

### Post by gradinaruvasile on 2011-07-01
This

```

#!/bin/bash
filename=$(zenity --file-selection --title "Select A File to Encrypt")
echo $filename

```

works correctly.

---

### Post by matt_symes on 2011-07-01
Hi

Have a look at dialog. That may do what you require as it's terminal based. 

IIRC, it does need to be installed though.

This is a very old write up on it, but it's still correct.

[http://www.linuxjournal.com/article/2807](http://www.linuxjournal.com/article/2807)

Kind regards

---

### Post by Habitual on 2011-07-02
```
me=$(whoami) # I used this so other users of the script won't have to change the --filename parameter on the next line.
key=$(zenity --title "Select key" --file-selection --filename=/home/$me/.ssh
```

---

### Post by kerry_s on 2011-07-02
```
key=$(zenity --title "Select key" --file-selection --filename=/home/$me/.ssh
```

missing a ")" on the end

```
key=$(zenity --title "Select key" --file-selection --filename=/home/$me/.ssh )
```

---

### Post by Habitual on 2011-07-03
Thanks kerry_s, you are correct.
Haste makes waste.

The alternative to zenity is yad and it should be in the REPOs. I have been playing with both and I am addicted to shell scripting all over again.

Preferring yad over zenity.

---

### Post by Habitual on 2011-07-03
> **LuniTux said:**
> ...I was wondering if there was an alternative to zenity that can do the same thing. I would prefer a terminal based program if possible.

Thanks,

yad is a fork of zenity and is way more flexible.

---

### Post by LuniTux on 2011-08-03
Sorry about the delayed response.

dialog works perfectly for what I need.

Thanks for all the suggestions though! :)

---

