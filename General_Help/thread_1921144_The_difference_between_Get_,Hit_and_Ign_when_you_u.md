---
title: "The difference between Get ,Hit and Ign when you update apt ???"
date: 2012-02-06
forum: General Help
---

### Post by soshiant on 2012-02-06
hey guys ?
 what is The difference between Get ,Hit and Ign when you update apt with :
sudo apt-get update


????:)

---

### Post by aasdfasdfg on 2012-02-06
According to [wojox]("https://launchpad.net/%7Ewojox") from [here]("https://answers.launchpad.net/ubuntu/+source/apt/+question/159133"),
> Hit means apt checked the package list the timestamps match and there are no changes.
 Ign means there are no changes in the pdiff index file so don't bother downloading it.


I can safely add that Get means the file was downloaded successfully.

---

