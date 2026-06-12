---
title: "An error occurred in Synaptic"
date: 2010-01-08
forum: General Help
---

### Post by Tapas Bose, India on 2010-01-08
Hallo everybody.
From four days each time I reload Synaptic, I got the following error:
```
W: Failed to fetch http://repository.cairo-dock.org/ubuntu/dists/karmic/Release.gpg  Could not resolve 'repository.cairo-dock.org'

W: Failed to fetch http://repository.cairo-dock.org/ubuntu/dists/karmic/cairo-dock/i18n/Translation-en_IN.bz2  Could not resolve 'repository.cairo-dock.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```
I can not understand what is it. Is it a temporary network problem? What I have to do? Please help.

---

### Post by mutex023 on 2010-01-09
Looks like the online repository is down.
Just go to Synaptic. Go to Settings > Repositories > Other software tab.
Uncheck the cairo-dock repositories, click on close and now reload.
You might later want to add another repository for cairo-dock that works.

---

