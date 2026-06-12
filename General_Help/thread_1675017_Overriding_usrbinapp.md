---
title: "Overriding /usr/bin/app"
date: 2011-01-24
forum: General Help
---

### Post by Githlar on 2011-01-24
Hello everyone!

Here's my problem: I have a program, let's call it "app", located in /usr/bin/app. Now, on my user account, I would always like to do a little pre-processing prior to executing /usr/bin/app.

I noticed that by default the first location in $PATH is $HOME/bin. So, I attempted to put a shell script in $HOME/bin that does the pre-processing and eventually calls /usr/bin/app when finished. Once I saved $HOME/bin/app and made it executable I ran 'which app' so I would know which version it would execute. The output of 'which app' was:
```
/home/xxx/bin/app
```
Looks good! However, when I went to run 'app' it ran the /usr/bin version. To make sure this was the case I commented out the call to the program I intend to run after the pre-processing in $HOME/bin/app. Nothing changed after I saved, which tells me that it's running /usr/bin/app.

Am I missing something?

---

### Post by Githlar on 2011-01-24
Doh! I tried everything except restarting bash! Haha! Sorry, guys.

---

### Post by djeikyb on 2011-01-24
Yup. Even reloading bashrc would do the trick:```
. ~/.bashrc
```

---

