---
title: "Firefox 5?"
date: 2011-06-11
forum: General Help
---

### Post by Sennaista on 2011-06-11
I just updated Natty and Firefox got updated to version 5. I have no beta PPA added though so what gives? :confused:

---

### Post by kostkon on 2011-06-11
Yeah, ffox5 beta is in the proposed repo, right now. It will be offered as a regular update when the final version is out.

Check if you have the proposed repository enabled in your software sources; open your software centre and select Edit &#8594; Software Sources.

---

### Post by Toz on 2011-06-11
Interesting. 4.0.1 is in the official repositories (at least the mirror that I'm connecting to). Open a terminal window and type in the following command:```
apt-cache policy firefox
```

Post back the results and lets see.

---

### Post by kostkon on 2011-06-11
And about the nature of the proposed repo:
> "Pre-released Updates (natty-proposed)". The testing area for updates. This repository is recommended only to those interested in helping to test updates and provide feedback.

---

### Post by chrisccoulson on 2011-06-11
[This]("http://askubuntu.com/questions/48035/why-is-natty-proposed-suggesting-an-upgrade-to-a-beta-version-of-firefox/") explains why you have the latest beta

---

### Post by Sennaista on 2011-06-11
Ok, that explains it. I do have the proposed repo turned on.

---

### Post by Frogs Hair on 2011-06-11
[http://mozilla.github.com/process-releases/draft/development_specifics/](http://mozilla.github.com/process-releases/draft/development_specifics/)

---

