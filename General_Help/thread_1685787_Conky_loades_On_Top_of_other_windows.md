---
title: "Conky loades On Top of other windows"
date: 2011-02-11
forum: General Help
---

### Post by Sinopa on 2011-02-11
[IMG]http://www.hannacam.net/screenshot.png[/IMG]


For some strange reason, Conky loades on top of other windows. First when I reload the conkyrc file under /.conkyx, then Conky loades under the other windows.

Is there something I can do about this?

---

### Post by Random_Dude on 2011-02-11
Is you problem because it loads that way when you boot?
If so, try this: [http://ubuntuforums.org/showpost.php?p=2309149&postcount=4](http://ubuntuforums.org/showpost.php?p=2309149&postcount=4)

---

### Post by Sinopa on 2011-02-11
> **Random_Dude said:**
> Is you problem because it loads that way when you boot?
If so, try this: [http://ubuntuforums.org/showpost.php?p=2309149&postcount=4](http://ubuntuforums.org/showpost.php?p=2309149&postcount=4)

That worked :)

Thank you Random_Dude :)

---

### Post by ajgreeny on 2011-02-11
For future reference, you can do exactly the same thing without a separate shell script, by using a slightly complex, but nevertheless still simple start command in Startup applications command box ```
bash -c "sleep 10; conky"
```including the " marks.

I need to use the same type of command for gmail-notify as well, or it starts before networking is up and running.

---

### Post by Random_Dude on 2011-02-11
> **Sinopa said:**
> That worked :)

Thank you Random_Dude :)

You're Welcome. ;)

Cheers :cool:

---

