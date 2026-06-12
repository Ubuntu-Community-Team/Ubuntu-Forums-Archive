---
title: "no downloads in firefox"
date: 2009-07-18
forum: General Help
---

### Post by techrascal on 2009-07-18
hello all
firefox  has stopped downloading any thing from the internet...not even saving a web page.
i tried to run it in safe mode but problem persisted.
checked the download location was selected as "ask me where to save"....

wat could probably be the problem??
thnx in advance..

---

### Post by techrascal on 2009-07-18
well ......is there any way to troubleshoot firefox throgh terminal????

---

### Post by michy99 on 2009-07-18
By any chance have you ever ran firefox using sudo firefox? If so, that is what is causing the problem.

---

### Post by techrascal on 2009-07-18
i used sudo firefox...still same thing..

it doesnot show any error but the save as window doesnot come up.....

i think a recent upgrade could have caused some problem ....but i dont know how to track it.....
any ideas would be appreciated..
thnx

---

### Post by michy99 on 2009-07-18
I was not saying to run sudo firefox, I was asking if you ever had, because it will mess up your settings. You need to run this command to fix it:```
sudo chown -R USERNAME:USERNAME ~/.mozilla
```Replace USERNAME with your username. For example, if your username was joe, you would run```
sudo chown -R joe:joe ~/.mozilla
```

---

### Post by techrascal on 2009-07-18
i already had used sudo firefox before in trying to fix this prob.....
i tried your command( chown -R....) also..but i still cant save a web page........
is their any alternative solution??
thnx

---

### Post by michy99 on 2009-07-18
What happens when you try to save a page? Start firefox from a terminal and try to save a page and see if you get any error message in the terminal.

---

### Post by y-lee on 2009-07-18
Try the advice given [Unable to save or download files]("http://kb.mozillazine.org/Unable_to_save_or_download_files")

---

### Post by jerome1232 on 2009-07-18
Is your disk full? What's the output of this
```
df -h
```

---

### Post by techrascal on 2009-07-20
great advice at that link....it worked..

thanks to all....

---

