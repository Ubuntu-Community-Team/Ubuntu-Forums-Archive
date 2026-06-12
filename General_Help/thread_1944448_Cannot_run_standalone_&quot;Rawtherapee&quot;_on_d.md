---
title: "Cannot run standalone &quot;Rawtherapee&quot; on double-click"
date: 2012-03-21
forum: General Help
---

### Post by The Bright Side on 2012-03-21
Hello Ubuntu fans! I hope you can help me out with this one.

I downloaded the latest version of the program "Rawtherapee" for Ubuntu 11.10, 64 bits. It's available as a .zip file from their web page, and I read in a forum somewhere that it is a standalone program that does not require installation, but just runs when you double-click the executable.

I unzipped the folder and double-clicked on a file called "rawtherapee" in it, but nothing at all happened.

Am I doing something wrong?

---

### Post by Paddy Landau on 2012-03-21
It is available in the Repository. Why not just install from there?

---

### Post by The Bright Side on 2012-03-21
Outdated...

---

### Post by Paddy Landau on 2012-03-21
> **The Bright Side said:**
> Outdated...
Oh, I see, it is very outdated.

In order to find the problem, run it from a terminal. Open a terminal. Change to the directory where you saved it. Type the following and press Enter:
```
./rawtherapee
```Let us know what happens.

---

### Post by The Bright Side on 2012-03-21
Hey Paddy!

Thanks, I wonder why I didn't think of that! I tried running from the terminal and I get:

The program 'rawtherapee' is currently not installed.  You can install it by typing:
sudo apt-get install rawtherapee

It's odd indeed. I must say I'm used to getting programs (if not from PPA) as .deb files or .tar.gz to compile myself (which I never got to work). This is the first time I come across a Ubuntu software distributed in a zip file...

Is there any other way to extract and run this? Did you ever encounter any programs that came packed into a zip?

---

### Post by Paddy Landau on 2012-03-22
> **The Bright Side said:**
> The program 'rawtherapee' is currently not installed.  You can install it by typing:
sudo apt-get install rawtherapee
Are you sure you put the "./" in front of the "rawtherapee"?
```
./rawtherapee
```

---

### Post by The Bright Side on 2012-03-22
Yeh I did, though not right away. It told me that a library was missing, so I installed that and then the program launched.

Unfortunately, it crashed when I double-clicked on an image I had imported. I'll keep Rawtherapee in mind while I toy around with Darktable for a while... Thanks for helping!

---

### Post by Paddy Landau on 2012-03-22
Glad you managed to get it running, if not properly.

If this thread has answered your question, please [mark it as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

