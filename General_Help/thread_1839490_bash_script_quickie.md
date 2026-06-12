---
title: "bash script quickie"
date: 2011-09-05
forum: General Help
---

### Post by spiky001 on 2011-09-05
Where is the correct place to put bash scripts so they can be executed from $. I have put them in home but I have to put complete path, I tried /usr/local/sbin but Permission denied.

---

### Post by sisco311 on 2011-09-05
In Ubuntu ~/bin is added to PATH if it exists.

---

### Post by papibe on 2011-09-05
> There are a couple of options:

The simpler is to use sudo to copy your script to /usr/local/bin.

This is what I do: I created my ~/bin and then modify the bash PATH variable so it includes my personal bin. This how it looks the line on my ~/.bashrc:
```
PATH=$PATH:$HOME/bin
```
Hope it helps,
Regards.

Look at sisco331's replay above.

---

### Post by sisco311 on 2011-09-05
The default .profile file already contains:
```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

```

---

### Post by papibe on 2011-09-05
:P Very cool, nice to know!

---

### Post by spiky001 on 2011-09-05
Thks sisco I created bin in home that works now, I did figure sudo cp  /usr/local/sbin but was unsure if it would execute but it did, I prefer to keep things neat, Bin in home is good cheers

---

### Post by sisco311 on 2011-09-05
You're welcome!

You have to be careful when you copy files to /usr/local/bin. If you want to allow anyone to run the script then set root:root as the owner and 0755 permissions. To allow only members of a specific group then set the owner to root:mygroup and 0750 permissions.

NOTE: Users only need read permission to execute a script.

See:  [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

PS: Don't forget to mark this thread as solved.

---

