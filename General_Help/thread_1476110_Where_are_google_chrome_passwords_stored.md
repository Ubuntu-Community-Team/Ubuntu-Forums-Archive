---
title: "Where are google chrome passwords stored?"
date: 2010-05-07
forum: General Help
---

### Post by hakermania on 2010-05-07
Where are they in the filesystem and how can I see them somehow (plugin, open with text editor or something?)

---

### Post by scottku on 2010-05-07
If you run chrome, go to the "wrench" menu on the upper right hand corner, select "Options", go to the "Personal stuff" tab, there is a button you can hit to show saved passwords.

---

### Post by hakermania on 2010-05-07
Thx for the answer but this isn't what I wanted to know. i want to know WHERE are the passwords stored...For example firefox's passwords are stored in /home/user/.mozilla/firefox/profilename/
In google chrome where are they stored at?

---

### Post by scottku on 2010-05-07
Google Chrome uses the XDG base directories to store its information.  So, its configuration info (and, presumably the passwords) are stored somewhere under the following directory:

~/.config/google-chrome

I don't know which specific file they are stored in, or what format they are in.

---

### Post by hakermania on 2010-05-08
Any other who knows where exactly are they sored and a prog/addon that export them in txt file or something readable?

---

### Post by marranzano on 2010-09-03
they are stored in ~/.config/google-chrome/Default/Login\ Data

to export to chrome-passwords.txt file:

```
$ sqlite3 ~/.config/google-chrome/Default/Login\ Data
$ sqlite> .output chrome-passwords.txt
$ sqlite> select origin_url, username_value, password_value from logins;
$ sqlite> .exit

```

taken from [here]("http://www.google.com/support/forum/p/Chrome/thread?tid=23ae64b3ab56a954&hl=en") and it works ;)

marranzano

---

### Post by vlke on 2011-03-26
I get the error message after this line:
sqlite> select origin_url, username_value, password_value from logins;

"Error: database is locked"

---

### Post by vlke on 2011-03-26
> **vlke said:**
> I get the error message after this line:
sqlite> select origin_url, username_value, password_value from logins;

"Error: database is locked"

I was reading the instructions from the browser so I had it open originally. When I tried it with Chrome closed, it worked.

---

### Post by cerberos on 2012-04-10
I just tried to follow these instructions and they very nearly worked. There was no errors, (other than database locked on the first try, so I closed Chrome) but the output file is empty (it was created though).

Any hints?

---

### Post by lukjad on 2012-09-08
Hi there, that would be because Chrome now encrypts it's saved passwords. I'm currently trying to find a solution to this as well, but I thought I would point this out for other people who wanter across this thread later looking for an answer.

---

### Post by afulldeck on 2012-09-08
What problem are you trying to solve with the chrome password storage location?

---

### Post by lukjad on 2012-09-09
I'm trying to export them so I can move my passwords to KeePass.

---

### Post by mydatespots on 2013-03-26
You probably want to use ChromePass, [http://www.nirsoft.net/utils/chromepass.html](http://www.nirsoft.net/utils/chromepass.html)

---

### Post by ulabunt on 2013-05-17
Chrome passwords are saved in gnome keyrings now. 
(see ~/.gnome2/login.keyring or ~/.local/share/login.keyring or something like that). 
Use 'seahorse' to browse the passwords.

---

