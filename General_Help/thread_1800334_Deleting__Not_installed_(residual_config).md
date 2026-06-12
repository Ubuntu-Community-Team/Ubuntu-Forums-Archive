---
title: "Deleting  Not installed (residual config)"
date: 2011-07-08
forum: General Help
---

### Post by xismyname on 2011-07-08
[SIZE=3]**Hi there **[/SIZE]

[SIZE=3]So I am just get straight to the point I am trying to completely delete the Not installed (residual config) packages in the synaptic package manager I did it before and it was OK but now when I mark a package for complete removal I am supposed to click the apply button right ???? :!: well guess what I cant the apply button doesn't go on ????:confused:

ohh yea i am running the latest version of ubuntu
[/SIZE]

---

### Post by JC Cheloven on 2011-07-08
Sure, nothing is changed until you press the apply button. Even then you're asked again.

To uninstall residual unused packages, from terminal:
```
sudo apt-get autoremove
```

Or even better, instal gtkorphan and run it.

Cheers

---

### Post by 73ckn797 on 2011-07-08
> **xismyname said:**
> [SIZE=3]**Hi there **[/SIZE]

[SIZE=3]So I am just get straight to the point I am trying to completely delete the Not installed (residual config) packages in the synaptic package manager I did it before and it was OK but now when I mark a package for complete removal I am supposed to click the apply button right ???? :!: well guess what I cant the apply button doesn't go on ????:confused:

ohh yea i am running the latest version of ubuntu
[/SIZE]
This was also a problem that I found with 11.04. You could try it from the command line:
```
sudo apt-get autoremove package name
or
sudo apt-get purge file name
```
That did not work for me along with several other commands. I just tried them again and it would not work. I have reverted back to 10.04 on my laptop and will do the same on this desktop computer tomorrow.

---

### Post by xismyname on 2011-07-08
worked like a charm thanx dude

---

### Post by xismyname on 2011-07-08
> **JC Cheloven said:**
> Sure, nothing is changed until you press the apply button. Even then you're asked again.

To uninstall residual unused packages, from terminal:
```
sudo apt-get autoremove
```Or even better, instal gtkorphan and run it.

Cheers

worked like a charm thanx dude

---

### Post by xismyname on 2011-07-08
> **73ckn797 said:**
> This was also a problem that I found with 11.04. You could try it from the command line:
```
sudo apt-get autoremove package name
or
sudo apt-get purge file name
```That did not work for me along with several other commands. I just tried them again and it would not work. I have reverted back to 10.04 on my laptop and will do the same on this desktop computer tomorrow.

it didn't work for me either but the gtkorphan worked nicely

---

### Post by JC Cheloven on 2011-07-11
> **xismyname said:**
> worked like a charm thanx dude

Glad it worked :)
If you can, take a moment to mark the thread as solved, so that others can search better ("thread tools" towards the top of the page).

---

