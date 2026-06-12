---
title: "Ubuntu as 1st option and windows 7 as 2nd option when computer starts"
date: 2011-06-01
forum: General Help
---

### Post by manish23march on 2011-06-01
[wubi] I have installed windows on c: and the ubuntu on d: drive.....
Is it poossible to make ubuntu as first option when computer starts???

---

### Post by iclestu on 2011-06-01
> **manish23march said:**
> I have installed windows on c: and the ubuntu on d: drive.....
Is it poossible to make ubuntu as first option when computer starts???

I think it normally does this as a default? 

There are gui's for altering grub's settings and default boot system.. I have kde-config-grub2 which you can get by

```
sudo apt-get install kde-config-grub2
```

There may be others....

---

### Post by sanderd17 on 2011-06-01
> **iclestu said:**
> I think it normally does this as a default? 

There are gui's for altering grub's settings and default boot system.. I have kde-config-grub2 which you can get by

```
sudo apt-get install kde-config-grub2
```

There may be others....

This will not work since it's a WUBI install. 

@OP: please mention that you installed it via WUBI in the title (you can just edit your post). I don't know enough of the windows bootloader to solve this.

---

### Post by iclestu on 2011-06-01
> **sanderd17 said:**
> This will not work since it's a WUBI install. 

@OP: please mention that you installed it via WUBI in the title (you can just edit your post). I don't know enough of the windows bootloader to solve this.

aaah - hence use of c:and d: etc. Thought it was just a bit of old windows terminology creaping in :)

Sorry guys, my prev post is rubbish! :)

---

