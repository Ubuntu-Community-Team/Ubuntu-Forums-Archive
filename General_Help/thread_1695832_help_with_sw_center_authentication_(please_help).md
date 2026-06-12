---
title: "help with s/w center authentication (please help)"
date: 2011-02-26
forum: General Help
---

### Post by rahulbest on 2011-02-26
i m unable to install enthing from s/w center or synaptic or from terminal...
it showing error like this->
 The action would require the installation of packages from not authenticated sources.

what to do????

PLEASE HELP I AM POSTING IT AGAIN coz no1 replied

---

### Post by sikander3786 on 2011-02-26
Go to Applications > Accessories > Terminal and run this command.

```
sudo apt-get update
```

It would refresh your software index and I hope you will be able to use Software Center and Synaptic later.

If there are any errors in the output, please post them.

---

### Post by rahulbest on 2011-02-26
Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-e

i get these kind of series of errors wen i try to update from terminal

---

### Post by sikander3786 on 2011-02-26
Go to Software Center > Edit > Software Sources and select the 'Main' server for your downloads.

Again run the same command in Terminal and copy/paste all the text here. Press # icon in post menu and paste your text in between the generated [code] tags for readability purposes as this will be a long output.

---

### Post by rahulbest on 2011-02-26
thnks sikandar it worked....

---

