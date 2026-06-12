---
title: "How to make your own show desktop icon."
date: 2009-07-21
forum: General Help
---

### Post by MadnessRed on 2009-07-21
I have seen tutorials posted on how to make your own show desktop link and they basically involve downloading a program and then writing a script to mimic pressing Control D. Whilst this works very well it is a bit of a long winded way of doing it.

If you want a simpler way to show desktop try this.

1) Download wmctrl
```
sudo apt-get install wmctrl
```

2) Right click on panel - select add to panel.
In the box which says command. Enter this.
```
wmctrl -k on
```

Fill in the rest as you desire.

Only downside is that it only shows desktop. Clicking it again will not bring back the windows.

(If you want a separate icon to bring them back. That can be done by 'wmctrl -k off'.)

---

