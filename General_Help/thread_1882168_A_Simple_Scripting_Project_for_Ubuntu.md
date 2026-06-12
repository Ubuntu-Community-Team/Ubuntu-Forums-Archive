---
title: "A Simple Scripting Project for Ubuntu"
date: 2011-11-16
forum: General Help
---

### Post by Dorakara on 2011-11-16
Hello,

I am a ubuntu user who has never really gotten into the more programing intensive side of linux and now would like to start getting my feet wet with what I feel would be a simple project.

You see, every once and a while my mozilla firefox will come up with an error saying I need to kill the process to get it to work again. Although this is easily done by entering system monitoring and clicking kill process, I figured the project seemed simple enough to make a script to do this instead.

If anyone can give me links to documentation or any code that may get me started on my small project, I would be greatly appreciative :)

I am currently using 10.10 at the moment in case that changes things :)

I look forward to your responses,

Sincerely,
Dorakara

---

### Post by Habitual on 2011-11-17
Since every good script must start off with a *bang*...
```

#!/bin/bash
kill $(pidof firefox-bin)
#EOF

```

save as say ~/bbff.sh (bye bye firefox?) then in terminal >
```
chmod 700 ~/bbff.sh
```

now you can use it on the desktop or run via alt+f2 or a menu entry, or a panel action.

[http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/) is an excellent resource.

HTH.

---

### Post by Dorakara on 2011-11-17
Thank you for your help Habitual, you made my life a little easier :)

now is the step:
chmod 700 ~/bbff.sh
needed after every time the file is edited to make it run again? Also thank you for the link I will for sure be looking at it :)

---

### Post by Dorakara on 2011-11-17
Well that was easy :)
After acquiring the kill Code from above I simply added as the next line:

which automatically starts firefox up after killing the process :) works great and I am happy with it. I hope to be able to do more of these "Home Improvement" type projects in the future :) thank you as well Habitual for giving me the link to that website, google also helped as well :)

---

