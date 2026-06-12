---
title: "Firefox not starting"
date: 2012-02-03
forum: General Help
---

### Post by Coolmariorocks on 2012-02-03
Hello, I tried launching firefox from the panel in ubuntu 10.10  and it does work kind of..  on the bottom panel it says starting firefox.. but it doesn't start..  when i run the command  "Firefox" in the terminal it gives me a message that says "/home/ray/bin/firefox: line 3: /home/ray/firefox/firefox: No such file or directory
/home/ray/bin/firefox: line 3: exec: /home/ray/firefox/firefox: cannot execute: No such file or directory"

when i run command sudo firefox

than firefox launches..  basically i want to know why isn't firefox 10  starting up?  I tried removing and reinstalling but that didn't work..  please note i have chromium installed.

---

### Post by Toz on 2012-02-03
It looks like its trying to execute a firefox command in your /home/ray/bin directory first and it isn't working. Try renaming that script:
```
cp /home/ray/bin/firefox /home/ray/bin/firefox.BAK
```
...and trying again, or from the command line:
```
/usr/bin/firefox
```

---

### Post by Coolmariorocks on 2012-02-03
I ran those commands. when i ran /usr/bin/firefox  it opened firefox..  but the when i try to launch it from the panel icon it doesn't work.  and when i typed firefox in the command line i still get the same message..

---

### Post by Toz on 2012-02-03
What does the following return?
```
which firefox
```

---

### Post by Coolmariorocks on 2012-02-03
I typed in which firefox and hit enter and got this

ray@ray-pc:~$ which firefox
/home/ray/bin/firefox
ray@ray-pc:~$

---

### Post by Toz on 2012-02-04
Rename the firefox file in your /home/ray/bin directory to something else, like firefox.BAK.

---

### Post by Coolmariorocks on 2012-02-04
> **Toz said:**
> Rename the firefox file in your /home/ray/bin directory to something else, like firefox.BAK.

There is a file named firefox.BAK

[IMG]http://i1122.photobucket.com/albums/l535/coolmario88/Screenshot.png[/IMG]

---

### Post by raja.genupula on 2012-02-04
hi copy that old file to some other place and then do as he said i mean rename to .BAK .

cheers
Raja

---

### Post by Coolmariorocks on 2012-02-04
Omg! It worked! I renamed Firefox  to Firefox.BAK and i clicked the icon on the panel and it launched with no problems!!  thank you! :)

---

### Post by raja.genupula on 2012-02-04
Thats great &  please mark the thread as solved  from thread tools and please remember marking for everytime after solving the issue .

Thank you .

---

### Post by Coolmariorocks on 2012-02-04
Ok. Topic is now marked as Solved :)

---

### Post by lovinglinux on 2012-02-07
Just to complete the information, NEVER run Firefox with *sudo*. That will mess the profile folder permission and cause many issues. Please make sure your **~/.mozilla** and **~/.mozilla/firefox** folders have the correct user ownership.

---

