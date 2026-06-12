---
title: "Chromium 18"
date: 2012-03-02
forum: General Help
---

### Post by granul on 2012-03-02
Hi!
I install Chromium on ubuntu 11.10, and I can't add home page in preference, I see at the top it says:  some preferences are managed by your administrator, how do I get rid of that so i can personalized my preference.

Thank you

---

### Post by Paddy Landau on 2012-03-02
How specifically did you install it?

---

### Post by granul on 2012-03-02
I installed via ubuntu depot, it is the first time i see this.

---

### Post by Paddy Landau on 2012-03-03
> **granul said:**
> I installed via ubuntu depot, it is the first time i see this.
Do you mean the Ubuntu Software Centre?

---

### Post by granul on 2012-03-03
> **Paddy Landau said:**
> Do you mean the Ubuntu Software Centre?

yes software center

---

### Post by granul on 2012-03-03
I installed Ubuntu 11.10 OEM from this web site [http://ualinux.com/](http://ualinux.com/), so the home page of chromium browser is always  [http://start.ualinux.com/](http://start.ualinux.com/) and I can't change it.

---

### Post by Paddy Landau on 2012-03-03
> **granul said:**
> I installed Ubuntu 11.10 OEM...
Ah. We cannot control what OEMs do.

I don't know whether or not it would work to purge Chromium and then reinstall it.
```
sudo apt-get purge chromium-browser
sudo apt-get install chromium-browser
```Warning: You may not end up with the same functionality, because I don't know what the OEM has done.

---

### Post by howefield on 2012-03-03
You could try renaming the ~/.config/chromium folder to force chromium into creating a new profile.

---

### Post by granul on 2012-03-03
thank you, but both solution did not work, i might just reinstall ubuntu 11.10 the orginal

---

### Post by lovinglinux on 2012-03-03
> **Paddy Landau said:**
> Ah. We cannot control what OEMs do.

I don't know whether or not it would work to purge Chromium and then reinstall it.
```
sudo apt-get purge chromium-browser
sudo apt-get install chromium-browser
```Warning: You may not end up with the same functionality, because I don't know what the OEM has done.

The OP already installed from the Software Center, so probably won't help purging it.

I would check if Chromium is actually installed from Ubuntu repositories or somewhere else. Looks like UALinux has their own repository and could be distributing a modified version of Chromium.

You can check that with Synpatic, by clicking the "origin" button, then selecting the [http://ualinux.com/ualinux-repo](http://ualinux.com/ualinux-repo) 

If that is the case, you could open the Software Sources application, then clicking the Other Software tab, then unticking all entries with [http://ualinux.com/ualinux-repo](http://ualinux.com/ualinux-repo) 

Then run an update and install chromium again. It should get the version from the Ubuntu repositories, if they are actually listed in the Software Sources. Keep in mind that you might have applications that only exist in that custom repository.

> **granul said:**
> thank you, but both solution did not work, i might just reinstall ubuntu 11.10 the orginal

I was about to suggest that. Good idea.

---

### Post by granul on 2012-03-03
Thank you, that solution work, I never though about that,

---

### Post by lovinglinux on 2012-03-04
> **granul said:**
> Thank you, that solution work, I never though about that,

Which one? Disabling the custom repository?

---

### Post by granul on 2012-03-04
> **lovinglinux said:**
> Which one? Disabling the custom repository?

I disable the custon repository, the ualinix

---

### Post by Paddy Landau on 2012-03-04
I'm pleased you managed to solve the problem. Now we know what the problem was.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

