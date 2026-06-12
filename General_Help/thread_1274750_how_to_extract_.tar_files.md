---
title: "how to extract .tar files"
date: 2009-09-24
forum: General Help
---

### Post by N4zgu1 on 2009-09-24
I recently downloaded a game but it comes in parts with the following name:

Game_Part1.tar and it also has part2.tar part3.tar and part4.tar

How can I extract them??

---

### Post by akakingess on 2009-09-24
I believe you can use Archive Manager to extract them, if it is not already installed (although it should be) you can add it through Synaptic.

---

### Post by tuxxy on 2009-09-24
Right click and goto extract here or in terminal you could something like

```
tar -xzvf file.tar.gz
```

---

### Post by N4zgu1 on 2009-09-24
I have already tried with extract here but it extracts the archives individually and I think that they should be united into a single archive like when you extract rar files.

---

### Post by bigboy_pdb on 2009-09-24
Try doing what is mentioned in this post on [LinuxQuestions.org]("http://www.linuxquestions.org/questions/linux-software-2/tar-split-question-605013/").

It says that you have to use "cat" to concatenate the archives.

**EDIT**: So in your case you'd use the command:
cat Game_Part1.tar Game_Part2.tar ... | tar -xvvf

---

