---
title: "Precise Pangolin libgoogle-dev not available after Upgrade"
date: 2012-05-26
forum: General Help
---

### Post by SeVeNeLeVeN on 2012-05-26
Can anyone help solve this issue regarding the Precise Pangolin Upgrade?

Issue Description:

After the Precise Pangolin upgrade, libgoogle-glog-dev & libgoogle-glog0 seem to  not be available. 

Without the -dev package, our program cannot be compiled. 
Without -glog0, it may not be dpkg'd. We need a solution for this problem pretty fast.

---

### Post by SeVeNeLeVeN on 2012-05-26
[Follow-Up Info]

*This error effects at least 1 members of our team*

This issue is linked to a bug report on Launchpad:
          [https://bugs.launchpad.net/asgard/+bug/999107](https://bugs.launchpad.net/asgard/+bug/999107)

---

### Post by SeVeNeLeVeN on 2012-05-26
This issue has also been addressed at AskUbuntu:

[http://askubuntu.com/questions/142504/google-glog-library-not-present-after-precise-pangolin-upgrade](http://askubuntu.com/questions/142504/google-glog-library-not-present-after-precise-pangolin-upgrade)

---

### Post by SeVeNeLeVeN on 2012-05-31
Solved by Ishaan Dalal (izx) who wrote on 2012-05-27:

Link: 
[https://bugs.launchpad.net/asgard/+bug/999107](https://bugs.launchpad.net/asgard/+bug/999107) 

"Guys:

Got here from Dan's AskUbuntu question.

1. Here's why it was pulled from Precise -- at the request of the Debian QA team: [https://launchpad.net/ubuntu/precise/amd64/libgoogle-glog0](https://launchpad.net/ubuntu/precise/amd64/libgoogle-glog0)

2. If a ppa will do, 0.3.1-1ubuntu1 (from Oneiric) appears to compile just fine on Precise."

Thank you for the help Ishaan, we really appreciate it.

---

