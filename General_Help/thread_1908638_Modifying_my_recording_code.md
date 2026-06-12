---
title: "Modifying my recording code"
date: 2012-01-13
forum: General Help
---

### Post by rmcellig on 2012-01-13
This is the code I use to record my radio show:

arecord -t wav -f cd -d 8800 /root/radioshows/intransition.wav 

Is there a way I can add parameters to the code that will display a time and date stamp?

---

### Post by ron999 on 2012-01-13
> **rmcellig said:**
> This is the code I use to record my radio show:

arecord -t wav -f cd -d 8800 /root/radioshows/intransition.wav 

Is there a way I can add parameters to the code that will display a time and date stamp?

Try this:-
```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); arecord -t wav -f cd -d 8800 /root/radioshows/$NOW-intransition.wav
```

---

### Post by rmcellig on 2012-01-13
Doesn't seem to work. All I get is a - before the name of the wav file and nothing else. I pasted the code you had in your last post.

---

### Post by ron999 on 2012-01-13
Do you get a response with these commands:-

```
echo $(date +"%Y-%m-%d-%Hh%Mm")
```

and 

```
date --help
```

---

### Post by rmcellig on 2012-01-14
Yes:


sh-4.1# echo $(date +"%Y-%m-%d-%Hh%Mm")
2012-01-14-12h07m

I also get a response to date --help which looks like a MAN file.

---

### Post by ron999 on 2012-01-14
How about this:-
```
arecord -t wav -f cd -d 8800 /root/radioshows/$(date +"%Y-%m-%d-%Hh%Mm")-intransition.wav
```

---

### Post by rmcellig on 2012-01-14
Thanks! I will give it a try.

---

