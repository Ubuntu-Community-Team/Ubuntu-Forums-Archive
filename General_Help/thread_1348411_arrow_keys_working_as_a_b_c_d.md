---
title: "arrow keys working as a b c d"
date: 2009-12-07
forum: General Help
---

### Post by deekshajain on 2009-12-07
on my vi editor my arrow keys display a b c d . i have to come out to insert mode to use it for direction movement.iam a newbie to ubuntu , so please tell the details of what to do . your help would be appreciated.

---

### Post by weemadarthur on 2009-12-07
That's the way it's supposed to work. 
When in command mode (what you are in when you press Escape), vi will interpret the arrow keys and move the cursor.
When in insert mode, the arrow keys are directly entered into the text. The characters you are seeing are the scan codes for the particular key you have pressed.

---

### Post by Vishnu V on 2009-12-07
You can use arrow keys in vi editor for navigation in insert mode after installing vim by
```

sudo apt-get install vim

```

---

### Post by ikarib on 2010-03-16
you don't have to install vim. Just copy default configuration file:
```
cp /etc/vim/vimrc ~/.vimrc
```

---

