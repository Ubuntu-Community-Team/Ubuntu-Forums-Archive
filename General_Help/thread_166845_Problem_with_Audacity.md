---
title: "Problem with Audacity"
date: 2006-04-27
forum: General Help
---

### Post by tc10b on 2006-04-27
Hi,

I've been using Audacity for quite a while now and it's been working fine letting me record and edit sounds.
The problem I have at the moment is that for some reason it now prompts me with an error message everytime it loads saying it can't find my sound card. I really don't understand it as I've been using it now for a while and it was fine. :confused: 

Can anyone help me?

The exact error message is the following

"There was an error initialiising the audio i/o layer. You will not be able to play or record audio. Error: Host Error"

Thanks in advance.

Tom

---

### Post by tc10b on 2006-04-28
I fixed it. \\:D/

For some reason the system sounds were interfering with it so I just switched them off and it works fine. I don't get it but at least it works!

---

### Post by tc10b on 2006-11-13
Hmm, I now have the same problem under dapper but the system sounds aren't interfering with it.

---

### Post by tocleora on 2006-11-17
I'm using Dapper and the way I got the error to go away is I unchecked everything under System > Preferences > Sound.  And by everything:

[LIST]
[*]Enable software sound mixing (ESD)
[*]Play system Sounds
[*]Enable System Beep
[/LIST]

I haven't tested it extensively yet but you might try that and see if that helps.

---

### Post by christhemonkey on 2006-11-17
Or try killing any running esd process:

```
sudo kill -9 esd 
```

---

