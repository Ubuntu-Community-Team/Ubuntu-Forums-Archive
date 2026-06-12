---
title: "Firefox and Flash - Sound drags behind video"
date: 2006-04-12
forum: General Help
---

### Post by Silver Streak on 2006-04-12
Yeah, I'm a new Ubuntu user; I've been using Ubuntu for a month or so now on my home PC. It's been an interesting experience - I'll post a testimonial sometime.

Anyways, whenever I watch a flash movie in Firefox, the sound and the visual always starts out synched, but as time goes on, the sound gets more and more out of sync with the video. (If it's important, the sound happens after it was supposed to.)

I've searched all over, and I've only seen topics dealing with flash sound not working completely. I would appreciate any help with this.

SS

---

### Post by vxj9219 on 2006-04-12
Lots of people including me have this problem...flash audio lag in firefox and mozilla browser. There was a discussion going on a few months back on how to fix it. 
[http://ubuntuforums.org/showthread.php?t=22672&highlight=firefox+audio+lag](http://ubuntuforums.org/showthread.php?t=22672&highlight=firefox+audio+lag)

See the last three pages of the thread. Looks like it worked for some people and didn't for others. I am yet to try it out myself. Read it and see if you are able to correct this issue on your computer.

---

### Post by Silver Streak on 2006-04-13
Thanks! It appears as if the problem's fixed. I've looked at several movies, and they all seem to not lag anymore. If anyone's curious, I followed the steps outlined in [this]("http://ubuntuforums.org/showpost.php?p=321288&postcount=44") post.

Problem hopefully solved,

SS

---

### Post by Silver Streak on 2006-04-14
GAAAAAAAAH!

Apparently, the fix disabled the REST of my sound... So now, there's only sound in flash. And it's STILL dragging.

Now, I noticed something in step six of [that]("http://ubuntuforums.org/showpost.php?p=321288&postcount=44") post, the one dealing with the esd config file:

```
[esd]
auto_spawn=0
**spawn_options=**
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-terminate -nobeeps -as 1
```

Notice the bolded line. Did the person forget to add something after the = sign? Is that what's causing all the silence?

SS

---

