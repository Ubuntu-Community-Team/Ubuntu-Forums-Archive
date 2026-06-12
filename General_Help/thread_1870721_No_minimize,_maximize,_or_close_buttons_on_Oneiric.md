---
title: "No minimize, maximize, or close buttons on Oneiric 11.10?"
date: 2011-10-27
forum: General Help
---

### Post by Zach_Ary on 2011-10-27
I updated to 11.10 yesterday after about a month without using Ubuntu. I'm pretty noob-ish so try to water down the instructions. (I can use terminal, I'm not THAT noob-ish)
So now I don't have any minimize, maximize, or close buttons on any window. Whether it be Firefox, Terminal, or the Software Center. It's really bugging me, so how do I get them back? And I'd like something permanent. (Don't want to have to type in a command every time I log in). Any help is appreciated. Thanks! :P

---

### Post by xianbei on 2011-10-27
have you tried resetting unity?

open a terminal, type:

```
unity --reset
```

---

### Post by Zach_Ary on 2011-10-27
Yeah, that works but as soon as I close terminal it stops working. Doing metacity --replace has the same effect as unity --reset. It used to do this on Natty too, but I just did metacity --replace every time I logged on and now I'm flat out annoyed. What should I do? :confused:

---

### Post by elliotn on 2011-10-27
> **xianbei said:**
> have you tried resetting unity?

open a terminal, type:

```
unity --reset
```

and u still don't have them try 
```
metacity --replace
```

that would work but u will look the bling bling effects.

have u installed gtk3?

---

### Post by Zach_Ary on 2011-10-27
Hey, thanks! After I did unity --reset, I logged out and back in, and now it works perfectly. Thanks again dude. /close :P

---

### Post by Alan.Brown on 2011-10-27
In Unity the buttons are at the very top of the screen on the Left Hand side - not in the application bar of the application. 

Alan

---

