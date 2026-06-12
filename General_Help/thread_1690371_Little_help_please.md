---
title: "Little help please"
date: 2011-02-18
forum: General Help
---

### Post by Ziton on 2011-02-18
I was setting up mythbuntu. I almost had it working.. I changed the backend from secondary to primary. I also updated. Now when I start ubuntuu I get a white terminal. It responds to commands but I don't know how to get back in.  Is there some way to restore it back before 
the messup?

---

### Post by aeiah on 2011-02-18
hmmm, so is changing from secondary to primary at fault, or the backup? :p shoulda done one at a time i guess.

can you access the terminal (Ctrl+Alt+F1) or through ssh? if so, have a look at the error logs:
```
dmesg
```

if there's too much being spat at you, use:
```

less /var/log/messages

```

i suppose it'll also be useful to check the xorg logs
```

cat /var/log/Xorg.* | less

```

---

### Post by Ziton on 2011-02-18
Using  (Ctrl+Alt+F1) I was able to log in and now have a terminal prompt name@linux:~$
I'm going to try some other things you suggested.

---

### Post by Ziton on 2011-02-18
I tried 
less /var/log/messages 
and got
bash:less/var/log/messages:no such file or directory

---

### Post by Ziton on 2011-02-18
cat /var/log/Xorg.* | less
What is the vertical slash before less?

---

### Post by williamts99 on 2011-02-18
> **Ziton said:**
> cat /var/log/Xorg.* | less
What is the vertical slash before less?

It is a pipe, usually below the backspace key on your keyboard.

---

### Post by Ziton on 2011-02-18
I somehow set it on web server Apache 2.
When I turn it off it says
  "stopping Timidity"
" stopping web server apache2"
 How do I get back in?

---

### Post by Ziton on 2011-02-18
This is one of the busiest forum Ive ever seen.

---

### Post by Ziton on 2011-02-19
I found it.
it was 
sudo service gdm stop
startx

---

