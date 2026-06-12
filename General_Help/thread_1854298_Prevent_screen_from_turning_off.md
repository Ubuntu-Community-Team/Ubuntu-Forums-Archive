---
title: "Prevent screen from turning off?"
date: 2011-10-04
forum: General Help
---

### Post by arcturus.red on 2011-10-04
Any way to do that in Oneiric? The "Turn off after" drop-down in the screen settings doesn't have a "never" option.

---

### Post by Toz on 2011-10-08
Here's a workaround that might help. 

Create a (hidden) file in your home directory called **.xprofile** with the following contents:
```
xset -dpms
```
...and make the file executable.

This will disable monitor blanking. You'll need to either log off and on again for it to take effect, or enter, in a terminal window:
```
xset -dpms
```
...for it to take effect immediately.

---

