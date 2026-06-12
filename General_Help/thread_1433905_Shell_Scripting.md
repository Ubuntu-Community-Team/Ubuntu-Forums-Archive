---
title: "Shell Scripting"
date: 2010-03-19
forum: General Help
---

### Post by killthemyth on 2010-03-19
Hey I'm n00b in shell scripting:

Jst need one help: 
s=/home/john/Desktop/folder/new.txt;

I need a shell script which will jst return "new.txt". I tried to use by first finding the last / and thn jst takin the substr but got bad subsitution error. Please help

thnks

---

### Post by mridkash on 2010-03-19
s=$(basename /home/john/Desktop/folder/new.txt);

---

### Post by killthemyth on 2010-03-19
thnks man..jst forget the concept of basename :)

---

