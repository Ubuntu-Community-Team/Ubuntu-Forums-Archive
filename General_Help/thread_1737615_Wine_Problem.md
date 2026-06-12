---
title: "Wine Problem"
date: 2011-04-23
forum: General Help
---

### Post by jquillian on 2011-04-23
When I try and use Wine to run a Windows program, I get this message.

program.exe is not marked as executable. if this was downloaded or copied from an untrusted source........... 

How can a program be marked executable? How is it possible to get passed this message and use Wine?

For that matter is there a way to disable all mechanisms that are designed to protect me against myself?

Thanks

James

---

### Post by robert9805 on 2011-04-23
Right click the file. Change the permission to allow as executable.

---

### Post by jquillian on 2011-04-23
Robert

The problem that I am having it that the execute choice does not remain checked.

---

### Post by Morbius1 on 2011-04-23
Gosh this sure does come up a lot. Look, wine doesn't care if the file is executable. Wine doesn't even have the capability to determine if a Windows executable has a Linux executable bit set. The problem is something called "cautious-launcher".

Fix it permanently - here's two ways: [http://ubuntuforums.org/showpost.php?p=10548141&postcount=8](http://ubuntuforums.org/showpost.php?p=10548141&postcount=8)

---

### Post by gandaran on 2011-04-23
> **jquillian said:**
> Robert

The problem that I am having it that the execute choice does not remain checked.
where is the location of the .exe file? move it to home/user and you wont have the problem.

---

