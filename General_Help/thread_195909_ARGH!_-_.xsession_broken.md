---
title: "ARGH! - .xsession broken"
date: 2006-06-13
forum: General Help
---

### Post by Masahiro on 2006-06-13
Hello,

I recently installed some software. In the readme it said to back up your .xsession file [in your home folder] but stupidly I overlooked it :-$  [I'm a newbie to Linux and thought that it would be revertable by removing the software].

I'm currently running under a failsafe session but I don't want to do so on a permament basis.

Could someone forward me a copy of the default file that you get after installing Ubuntu, or another working copy?

Many thanks! :D

---

### Post by blackjack6.21.91 on 2006-06-13
Could you tell me where the file is located?

---

### Post by zxee on 2006-06-13
I think that you can get ubuntu to generate the file for you by-although there might be a simpler way-creating a new user (sudo adduser) and then copying that file to your current user.
Hope that helps.

---

### Post by Masahiro on 2006-06-13
On dapper, in the user's account that was created during setup's home folder [it's hidden in File Browser unless you press CTRL and H.]

Also, I tried creating a new user and I looked at the other account on this computer, but it's only on my account [which I created when installing.]

---

### Post by mlind on 2006-06-13
You can just remove it if you don't need it. It's contents are execute when X terminal
session is started.  On current Dapper, user's $HOME doesn't contain the file by default.

---

### Post by Masahiro on 2006-06-14
Thank you!

Fixed now.

---

