---
title: "Hotkey shortcuts manager"
date: 2012-04-02
forum: General Help
---

### Post by alpa8le on 2012-04-02
Hello,
I was looking for something which is equivalent to Spark([http://www.macupdate.com/app/mac/14352/spark](http://www.macupdate.com/app/mac/14352/spark)) app in OS X.
What I want to do is, run a script with a hotkey.
I tried gconf-editor, I couldn't get it working.
I want the script to paste the output to the webpage I am in when I type it's shortcut (ex. T)
Thanks in advance.

---

### Post by stinkeye on 2012-04-02
Just put the path to the script in keyboard shortcuts.

---

### Post by alpa8le on 2012-04-02
I did it. But it's working in background. ( a python or a bash script ) how can I actually make it print to the messagebox i am on?

---

### Post by stinkeye on 2012-04-02
> **alpa8le said:**
> I did it. But it's working in background. ( a python or a bash script ) how can I actually make it print to the messagebox i am on?
I thought that would be part of the script and the shortcut key invokes
the script.
What do you want the script to do?
Have a look at **Autokey**

---

### Post by alpa8le on 2012-04-02
I am trying to do this in a web browser:
while True:
    print "Test"
just this...

---

### Post by alpa8le on 2012-04-02
/home/alp/literal.py result:

Error while trying to run (/home/alp/literal.py)
which is linked to the key (<Shift><Control>r)

python /home/alp/literal.py result:
It runs in background.

---

### Post by alpa8le on 2012-04-05
Thanks, AutoKey was what I am looking for.

---

