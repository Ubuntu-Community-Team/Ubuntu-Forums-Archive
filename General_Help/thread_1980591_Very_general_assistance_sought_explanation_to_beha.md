---
title: "Very general assistance sought: explanation to behaviour from bash string"
date: 2012-05-15
forum: General Help
---

### Post by SuaSwe on 2012-05-15
Hi all,

I'm baffled by the function and action of a bash string, pasted below. **[color="red"]Please do not run it if you don't know what it does[/color]** - as I have discovered to my detriment, it can cause what appears to be a kernel panic which at least in my laptop's case results in a total lock-up. 

The string is '<removed once answer was obtained>'

When run it outputs something like:

[1] 12345     # the latter is a random number, not sure what it refers to

Can anyone explain what it does? I have tried monitoring syslogs, kern.log and top during the crash to see if I can spot what happens, but so far I have not gleaned any clues!

---

### Post by idoitprone on 2012-05-15
> **SuaSwe said:**
> Hi all,

I'm baffled by the function and action of a bash string, pasted below. **[COLOR=red]Please do not run it if you don't know what it does[/COLOR]** - as I have discovered to my detriment, it can cause what appears to be a kernel panic which at least in my laptop's case results in a total lock-up. 

The string is '_(){ _|_&}; _'

When run it outputs something like:

[1] 12345     # the latter is a random number, not sure what it refers to

Can anyone explain what it does? I have tried monitoring syslogs, kern.log and top during the crash to see if I can spot what happens, but so far I have not gleaned any clues!

I am not sure the exact code of the string, but it seems to be another variant of a fork bomb

[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

If its eats all your resources cause it to freeze, then it probably is a fork bomb

I guess its someone idea of a practical joke

---

### Post by SuaSwe on 2012-05-15
That makes good sense based on what I saw - gonna edit my post and make it unusable to safeguard the forum crowd! 

I wonder how such a thing could be prevented from working... hmmm...

---

### Post by idoitprone on 2012-05-15
> **SuaSwe said:**
> That makes good sense based on what I saw - gonna edit my post and make it unusable to safeguard the forum crowd! 

I wonder how such a thing could be prevented from working... hmmm...

Dont bother preventing it, but try to configure your system so you can fix it. One was is to limit the amount of process.

Just look at the wikipedia entry on defusing fork bomb

---

### Post by SuaSwe on 2012-05-15
Yeah, had a read of it - good info there! Thanks muchly for your help. :)

---

