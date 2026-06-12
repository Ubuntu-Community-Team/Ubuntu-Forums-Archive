---
title: "Fake pulse audio wine support"
date: 2010-10-11
forum: General Help
---

### Post by Lolpanda on 2010-10-11
Okay, so I know that if you set the Audio driver to OSS and preface any wine app with "padsp" you can make wine and pulseaudio play nice without recompiling with the fedora pulseaudio patch. (Why they havent incorporated this over all..I cant even imagine, but I can guess its stupid)

What I'm wondering is if I take the wine binary under /usr/bin, rename it "wine_real"

and create a bash script, named "wine", that says 


```


#! /bin/bash

padsp wine_real


```

And add that to /usr/bin/

Would that be the samething as adding "padsp" to any wine app, just you know, without having to do add that to each app? Or would that break wine?

---

