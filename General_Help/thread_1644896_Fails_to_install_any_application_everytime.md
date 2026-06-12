---
title: "Fails to install any application everytime?"
date: 2010-12-13
forum: General Help
---

### Post by cisco21c on 2010-12-13
Hi, I recently got Ubuntu up running on my HP DV1000 laptop. The problem I started noticing is that whenever I were to install packages via software center or even from the web. They simply won't install. After I enter my password it just hangs and won't continue forward. What's wrong here? I have a screenshot of where it hangs every time.

[[IMG]http://i21.photobucket.com/albums/b273/cisco21c/th_Screenshot.png[/IMG]]("http://i21.photobucket.com/albums/b273/cisco21c/Screenshot.png")
Click it to make it bigger.

---

### Post by oldos2er on 2010-12-13
Can you run **sudo apt-get update && sudo apt-get upgrade** in a terminal, and paste the output here?

---

### Post by cisco21c on 2010-12-13
Here it is: [http://pastebin.com/imcPgWhE]("http://pastebin.com/imcPgWhE")

---

### Post by oldos2er on 2010-12-14
So if you run ```
sudo apt-get install <package name>
``` does it work? Btw, you can just paste the terminal output into your post.

---

### Post by cisco21c on 2010-12-14
Yes, installing through terminal works, but I'm just curious why the other won't work,

---

