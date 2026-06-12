---
title: "having hard time saving document..."
date: 2009-09-29
forum: General Help
---

### Post by meluzi02 on 2009-09-29
Hello..

I have a hard time saving my document, this was actually occurred when I tried to save my document in open office writer to .xml extension,

there's a message saying that you have to install JRE...

can you please help me solve regarding this problem..

tnx in advance...

looking forward to it.. 

:(

---

### Post by credobyte on 2009-09-29
Have you tried installing this "JRE" ?

```
sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by eg0n on 2009-09-29
JRE stands for Java Runtime Environment. It's quite easy to do that with add/remove application. Just do a search for java runtime and select to install Java Runtime 6.

---

### Post by meluzi02 on 2009-09-30
I have already tried that code...but unfortunately it doesn't take effect...

it says 

**E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. **

i do not know what does that means...

:(

---

### Post by credobyte on 2009-09-30
```
sudo dpkg --configure -a && sudo apt-get install sun-java6-jre sun-java6-plugin

```

---

### Post by meluzi02 on 2009-09-30
I already did it..
after done it says

**E: The package skype needs to be reinstalled, but I can't find an archive for it**

it happens that this package was being interrupted upon installation and now I am trying to re-install this one but an error occurred...there's a message saying that either the package is being corrupted or i am not allowed to install the said package...

---

### Post by EleyTaronia on 2009-09-30
Really a educative and informative post, the post is good in all regards,I am glad to read this post.

---

### Post by credobyte on 2009-09-30
Did you installed Skype from Mediabuntu ( if not, the whole reply will be useless ) ?

```
sudo apt-get install -d skype

```What it'll do is download skype package, without installing it. If it tries to reinstall it, launch it again and it should fix your issue.

---

### Post by meluzi02 on 2009-09-30
I am glad that you have replied in order to help me with my problems

and I'm sorry for being so inquisitive...

thanks again...

---

