---
title: "PANIC: $PATH fail... Is there a way to undo?"
date: 2011-11-19
forum: General Help
---

### Post by zia.newversion on 2011-11-19
I was trying to:
```
$PATH=$PATH:<some-path-here>
```

and I did:
```
$PATH=<some-path-here>
```:mad::mad::mad:


Now
```
~/$ echo $PATH
```
gives
```
<some-path-here>
```
not
```
<all-bin-paths>:<some-path-here>
```

And I no longer remember what those <all-bin-paths> were!
Is there another environment variable which stores <all-bin-paths> or is there a way to recover it?:-k

Please don't say I'm screwed big time...:sad:

---

### Post by VCoolio on 2011-11-19
You need to do ```
PATH=$PATH:/your/path
```so delete the $ you have at the start of your line. Assuming you did this in ~/.bashrc or ~/.profile, just logout and back in.

---

