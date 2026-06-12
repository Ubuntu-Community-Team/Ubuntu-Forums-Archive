---
title: "Google Chrome Profile Problem"
date: 2010-09-02
forum: General Help
---

### Post by Sef on 2010-09-02
I am getting a message when I start google [s]chrome[/s] chromium from the ppa in 10.04, Lucid Lynx, that says 

"Your profile could not be opened correctly.

Some features may be unavailable. Please check that the profile exists and you have permission to read and write its contents." 

How do I fix this problem?

---

### Post by luceerose on 2010-09-02
Never seen that problem before.
I've found a lot less problems with the beta at the moment, though.
I would try installing the beta.

Using this method wil let you install through Synaptic & give you a choice between installing the stable, beta or unstable release.
In terminal;
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
Add to /etc/apt/sources.list;
```
deb http://dl.google.com/linux/deb/ stable non-free main 
deb http://dl.google.com/linux/deb/ testing non-free main
```
Then install through Synaptic.
I believe the packages are called google-chrome-stable, google-chrome-beta & google-chrome-unstable. You can only install one.

---

### Post by DeMus on 2010-09-02
Did you do a fresh install of the OS? Are you still owner of the home drive with the Chrome profile? I tried finding it but it is hidden so far away in the home folder that I did not succeed.
What else did you do before this happened?

---

### Post by Sef on 2010-09-03
> Did you do a fresh install of the OS? Are you still owner of the home drive with the Chrome profile? I tried finding it but it is hidden so far away in the home folder that I did not succeed.
What else did you do before this happened?

I have had the [s]chrome[/s] chromium from the ppa on here since about April when I installed Lucid.  I am the only person on the computer, but where would I check to see that I am still the owner?

---

