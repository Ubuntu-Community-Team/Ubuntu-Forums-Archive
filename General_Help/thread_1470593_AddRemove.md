---
title: "Add/Remove"
date: 2010-05-03
forum: General Help
---

### Post by cazador31 on 2010-05-03
By accident I uninstalled the ADD/REMOVE program

I need help getting it back

I am using Portable Ubuntu Redux

---

### Post by itiswhatitis on 2010-05-03
I am not familiar with the redux versions, and have nothing like that on my system...  what is the ADD/REMOVE program?  What does it do?

---

### Post by QIII on 2010-05-03
Do you mean the Software Center?  Synaptic?

---

### Post by WorMzy on 2010-05-03
Run in a terminal: ```
sudo apt-get install software-center
```

---

### Post by cazador31 on 2010-05-03
No it's not synaptic

The one I am looking for is in the System pull down menu

Not sure what it is exactly called, but it's where you can add or remove files

---

### Post by itiswhatitis on 2010-05-03
Add/Remove programs or files?

Was it under System->Administration or System->Preferences?

Update Manager?

---

### Post by QIII on 2010-05-03
Under System | Administration?

---

### Post by cazador31 on 2010-05-03
Yes, the Update manager

It is gone

---

### Post by WorMzy on 2010-05-03
```
sudo apt-get install update-manager
```

---

### Post by QIII on 2010-05-03
Do you remember if it was update-manager-core that you uninstalled?


Edit:  Have to go to bed.

What you likely will need to do is go to the terminal and execute

```
sudo apt-get install update-manager
```

Edit again:  Tired.  I took out adding update-manager-core, since that is for managing version upgrades.

---

### Post by itiswhatitis on 2010-05-03
```

sudo apt-get install update-manager

```

That should put it back.  :-)

---

### Post by itiswhatitis on 2010-05-03
If you just deleted the menu option, you can add it back by going to

System->Preferences->Main Menu

The file location is:  /usr/bin/update-manager

---

### Post by QIII on 2010-05-03
To add to itiswhatitis...

When you do what he says, you will get a nice little GUI with a lot of  check boxes.

Expand "System" on the left and click "Administration".  Somewhere in  there, you will find "Update Manager".  Make sure it is checked.

Provided, of course, you haven't actually uninstalled it.

---

### Post by Keith1212 on 2010-05-03
I installed the add/remove program from Software Center before i updated to 10.04. Now the add/remove program is gone. It was located on system>preferances I belive. It's not in the Software Center anymore either. Maybe this is because they updated the Software Center to make adding/removing apps easier?

---

