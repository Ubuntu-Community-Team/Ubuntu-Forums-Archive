---
title: "KMess is crazy! I can't remove logs!"
date: 2011-06-26
forum: General Help
---

### Post by micael3000 on 2011-06-26
Hello...

My KMess went crazy today after a forced restart (cutting of the power supply)... I had one chat opened, and this one chat had the logs affected, every time I open this chat again I see the logs from the last minutes before the shutdown... I have already delete this logs on ~/kmess/2011/06/ (where it is saving) and nothing happens (still shows the old logs!!!!!).
The new ones are saved on this folder (on the same file), but when I open the chat window with this person I cannot see them, just by opening the file manually.

Could anyone help me? :s

Thanks.

---

### Post by 2048Megabytes on 2011-06-26
Have you tried uninstalling and re-installing the program you are having problems with?

---

### Post by deserthowler on 2011-06-27
You might want to use 
```
sudo apt-get autoremove kmess
```
to remove things completely and then reinstall.

Earl

---

### Post by micael3000 on 2011-06-27
Hello!

I am hoping for a solution that does not evolve purging kmess... :/
Something like "KMess reads your chat history from another place, that is why it stays there even after being deleted... Try on this folder /A/B/C". :)

Thanks!

---

### Post by micael3000 on 2011-07-04
I have formatted my computer and then KMess 'restarted' it's logs.

Just for the records, KMess keeps lots of information in ~/.kde/share/apps/kmess...

There is probably where you need to go for fixing this issue.

---

