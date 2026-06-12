---
title: "skype multiple instances - how do I download python"
date: 2012-02-23
forum: General Help
---

### Post by dockalek on 2012-02-23
Hi, I'm trying to solve multiple instances with skype: skype won't start saying that there might be another instance running. And before that it always wants me to agree to the Terms and Conditions over and over. 
I found that this might solve it, but I don't know what to do with it. Shall I just drag it to terminal line after line. So, basically I need more help with downlloading python in the first place.

[http://ubuntuforums.org/showthread.php?t=1011348&highlight=skype+single+instance](http://ubuntuforums.org/showthread.php?t=1011348&highlight=skype+single+instance)

Thank you

---

### Post by winh8r on 2012-02-23
To get python, open a terminal and enter:


```
sudo apt-get install python
```

this will check to see if you have the latest version installed and offer you the latest version if you haven't.

As for the skype issue , the thread you refer to seems to resolve the issue from what I read, so you are on the right track there.

you can copy the code to an empty text file and give it a name ending in .py then run it as a python script.

just move to the directory where you have saved the script using the cd command then enter the name of the script at the command prompt

for instance:

```
examplename.py
```

and it should run ok.

---

### Post by dockalek on 2012-02-25
Hi, and thank you.
I coppied it to gedit, named it skyppe.py saved in ~/Templates. Tried to run it, being in the right directory with "skyppe.py" or "python skyppe.py"
none of those worked. ("no such file or directory")
I tried to move the file to usr/local/bin but I couldn't do that. So there's probabl something I'm missing out. Does it matter how you name the file and where you save it? And can you just run it like that, or you have to run it as root?
thank you

---

