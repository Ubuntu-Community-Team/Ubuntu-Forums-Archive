---
title: "How can I update a repo manually?"
date: 2011-06-22
forum: General Help
---

### Post by CoreyB. on 2011-06-22
My ISP is blocking medibuntu.org so that hasn't been updated on my machines since the end of April.  I can still access it via proxy sites so is it possible to download certain files and place them on the right spots in my Ubuntu installation and have it tell me if something is out of date or not?

Thanks a ton!

---

### Post by haqking on 2011-06-22
> **CoreyB. said:**
> My ISP is blocking medibuntu.org so that hasn't been updated on my machines since the end of April.  I can still access it via proxy sites so is it possible to download certain files and place them on the right spots in my Ubuntu installation and have it tell me if something is out of date or not?

Thanks a ton!

Strange, have you tried changing your DNS servers ?

---

### Post by haqking on 2011-06-22
> **CoreyB. said:**
> My ISP is blocking medibuntu.org so that hasn't been updated on my machines since the end of April.  I can still access it via proxy sites so is it possible to download certain files and place them on the right spots in my Ubuntu installation and have it tell me if something is out of date or not?

Thanks a ton!

did you recently do an upgrade ?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by CoreyB. on 2011-06-22
Yeah, I tried changing my DNS servers, but it is still blocked.

Anyways, does anyone know how/if I can update a repo, specifically medibuntu, manually?

---

### Post by Gyokuro on 2011-06-23
Maybe you can try to rsync the complete updates as shown here: [https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror) and change the paths for what you need.

HTH

---

### Post by life in color on 2011-06-23
Open Synaptic Package Manager go to Settings->Repositories. A new window should open up called 'Software Sources' go to Other Software then click the Add line, you may need a PPA URL though not really sure, give it a try and tell me what happens.

---

### Post by CoreyB. on 2011-06-23
Thanks for the suggestions, I'll look at the rsync option later.

But isn't there some simpler way to download a few files from packages.medibuntu.org so apt can look at those and notify me what, if anything, needs updating?

---

