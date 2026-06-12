---
title: "Adding a application to &quot;run application&quot;"
date: 2012-02-28
forum: General Help
---

### Post by duub7 on 2012-02-28
Hello,

I have a question - how can I add an application to "run application" (alt + f2)

I downloaded an application, unpacked it and can run it successfully from its launcher. But i cant run it from "run application" just by writing its name there like i do with firefox or other applications like that.

I am using ubuntu 11.04.

Thank you for your help :)

---

### Post by papibe on 2012-02-28
Hi duub7.

It probably won't run because it's within the directories on the variable $PATH.

I see 2 options:
[LIST]
[*]Add the path where the app is on your .bashrc. For example you can add a line at the end of the file:
```
PATH=$PATH:/path/to/your/app
```
[*]or put the application on your ~/bin, which is autocratically added to your $PATH if exists.
[/LIST]
In both cases you would have to restart your machine.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by efflandt on 2012-02-28
Actually if you **mkdir ~/bin** all you have to do for that directory to end up in your $PATH is log out of X and back in (don't need to totally restart the computer).  When you log in is when ~/.profile automagically includes your personal bin in your $PATH.

---

