---
title: "Can not install RSS Owl"
date: 2011-01-26
forum: General Help
---

### Post by Kymus on 2011-01-26
I am following the step by step directions as posted on the RSS Owl site here.

I added the GnuPG Key File, and I also added the repository (deb [http://packages.rssowl.org/ubuntu](http://packages.rssowl.org/ubuntu) **maverick** main).

I close, reload, and get this loving message:

> Failed to fetch [http://packages.rssowl.org/ubuntu/dists/maverick/Release](http://packages.rssowl.org/ubuntu/dists/maverick/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Is there something obvious I'm missing?

---

### Post by Frogs Hair on 2011-01-26
If your are using 9.04 ( now unsupported) as shown on your user information , that would explain why you can't connect to all the required sources.
 
I have seen the same messages at times and tried again at a later time and have been successful .

---

### Post by Kymus on 2011-01-26
Naw, I updated to 10.10 last night.

So I guess I should just try again some other time and like with most things related to technology it will magically work?

---

### Post by Kymus on 2011-01-27
bump

---

### Post by Halikar on 2011-01-27
I have a fresh install of 10.10 and am getting the same error. And so far, this is the only report I've been able to find on the issue. :)

---

### Post by Kymus on 2011-01-27
Interesting that we are both experiencing this with fresh installs.

I've created a thread at the RSS Owl forum, though looking at the forum activity there, I am not expecting a reply anytime soon.

---

### Post by Halikar on 2011-01-27
I do want to note, I've had no trouble manually downloading and using RSS Owl. I just thought it would be easier to have access to the repository for potential updates.

---

### Post by Frogs Hair on 2011-01-27
> **Kymus said:**
> Naw, I updated to 10.10 last night.

So I guess I should just try again some other time and like with most things related to technology it will magically work?

No, I have had times when I could not connect to sources because of temporary conductivity problems , nothing magical involved .

---

### Post by Kymus on 2011-01-28
Pardon my sarcasm. I've noticed many times with technology things magically fix themselves overnight. It drives me mad, because it makes no sense.

---

### Post by Kymus on 2011-01-28
I got RSSOwl 2.06 to install. I went to [GetDeb]("http://www.getdeb.net/updates/Ubuntu/10.10#how_to_install") and picked up a package from there. After the install, I got the same error I got before (at least, I believe it was the same). I don't know if this was related to the current install I was doing or if it was simply whining at me in regards to my previous attempt to add it to the repository. 

If this works for you Halikar, I'll mark this thread solved.

---

### Post by Halikar on 2011-01-28
That does appear to have done the trick. Thanks much.

---

