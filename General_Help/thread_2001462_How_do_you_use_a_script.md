---
title: "How do you use a script?"
date: 2012-06-10
forum: General Help
---

### Post by Yankees1327 on 2012-06-10
I am running on an ubuntu install disc, and chose try ubuntu rather than installing it. I am assuming that is the same thing as Ubuntu Live. I downloaded a script called bootinfoscript that I need to run, tried doing [sudo ./bootinfoscript] and also tried double clicking the actual script, neither work. When I double click the script, it opens terminal and closes it almost instantly. Is there something I am doing wrong?

---

### Post by drs305 on 2012-06-10
Yankees1327

Welcome to the Ubuntu Forums!

If you are in the same directory as the script:

```
chmod a+x bootinfoscript
sudo bash bootinfoscript
```
The first command allows the script to be executed; the second will start it.

---

### Post by papibe on 2012-06-10
Hi Yankees1327.

If the script run ok, look for a file called RESULTS.TXT in the same directory. 

If not, try again open a terminal, make sure the script is in the directory by listing the files:
```
ls
```
If not, it maybe in Downloads, so 'cd' to it:
```
cd Downloads
```
Once you see the script run it like this:
```
sudo bash boot_info_script*.sh
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by Yankees1327 on 2012-06-10
Thank you to both of you, it worked. I just wasn't in the right directory I guess.

---

### Post by papibe on 2012-06-10
:D great!

Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

