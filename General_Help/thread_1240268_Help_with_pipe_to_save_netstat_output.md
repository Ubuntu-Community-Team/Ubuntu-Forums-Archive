---
title: "Help with pipe to save netstat output?"
date: 2009-08-14
forum: General Help
---

### Post by VipX1 on 2009-08-14
I want to see netstat. I've no Gnome install. Using the terminal there's too much data and I can't read it. How can I get the output from netstat to go to a file.
i.e.
```
sudo netstat | file1
```
Can anyone write that command for me, thanks...

---

### Post by bear24rw on 2009-08-14
you can do
```
netstate | less
```
and then use down arrow key to scroll and q to quit
or to output to file
```
netstate > myfile.txt
```

---

### Post by VipX1 on 2009-08-14
Brilliant, Thank you.

---

### Post by slakkie on 2009-08-14
Just a heads up, if you need to write a file as root the > (redirector) will not work, since it will be executed as your user. You can use tee for that:

```

# Same as ls > file
ls | sudo tee file

# To append to a file
# same as ls >> file
ls | sudo tee -a file

```

---

