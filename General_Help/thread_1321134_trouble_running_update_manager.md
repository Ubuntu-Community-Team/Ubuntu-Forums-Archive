---
title: "trouble running update manager"
date: 2009-11-09
forum: General Help
---

### Post by hambidextrous on 2009-11-09
When I try to run the update manager I get the following message.

In a box titled: Could not download all repository indexes

Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Not sure how to fix so I can get new updates.  I installed google chrome recently, not sure it that is related.

Thanks in advanced.

---

### Post by michy99 on 2009-11-09
You can disable that particular repository. You won't get any updates from that repository, but everything else should work.

---

### Post by hambidextrous on 2009-11-09
where do I go to disable it?

---

### Post by michy99 on 2009-11-09
System->Administration->Software Sources. 'Other Software' tab. Uncheck the problem repository.

You can enable it again later to see if they have fixed the problem.

---

### Post by hambidextrous on 2009-11-09
That seems to have fixed it for now.  Thanks!

---

