---
title: "3rd Party Software Source Not Visible"
date: 2009-10-26
forum: General Help
---

### Post by Twelveone on 2009-10-26
Hi,

I'm running Jaunty (9.04) and have added a 3rd party software source pointing to our local repository and it is not visible in Synaptic. 

The APT line I entered was "deb [http://cascade-dc1/repository/stable](http://cascade-dc1/repository/stable) binary/"

We have used the same setup in Hardy (8.04) for over a years now with no issues.

Any ideas what the problem might be?

Thanks

Stewart

---

### Post by pricetech on 2009-10-26
Have you reloaded the package information since adding the repo ???

---

### Post by Twelveone on 2009-10-26
Hi,

I did reload after I added the repo Pricetech. 

I think I've solved it though. All the apps in the repo are compiled for hardy so won't be recognised as valid for Jaunty.

Correct me if I'm wrong?

Thanks

Stewart

---

