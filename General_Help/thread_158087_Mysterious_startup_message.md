---
title: "Mysterious startup message"
date: 2006-04-10
forum: General Help
---

### Post by Carandol on 2006-04-10
I've started getting a message on screen at login, which says:

"Your $HOME/.drnrc file has incorrect permissions and is being ignored. This prevents the default session aqnd language from being saved. File should be owned by user and have 644 permissions." 

The file mentioned doesn't seem to be there at all (either in the /home directory, or /home/<myname>, with hidden files showing. 

Anyone any idea how I can get rid of this message?

---

### Post by ubernoob on 2006-04-10
First of all... i think it is .dmrc and not .drnrc

try:
```
ls -al ~/.dmrc
```

if that doesn't exist, do:
```
touch ~/.dmrc
```

then you do:
```
chmod 600 ~/.dmrc
```

---

