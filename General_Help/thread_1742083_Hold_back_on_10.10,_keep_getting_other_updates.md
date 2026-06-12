---
title: "Hold back on 10.10, keep getting other updates?"
date: 2011-04-28
forum: General Help
---

### Post by jlbrewer on 2011-04-28
...and the answer isn't "use LTS". ;)  Maybe the next LTS whenever that comes out (12.whatever?), but we needed 10.10 for the ATI drivers.

Anyway, 11.04 has hit and since I'm dealing with office machines and software developers who expect a stable environment, I want to hold back 10.10 as long as possible (or at least "as long as I need to test things"), both on desktop and server installs.  I'm looking at 130+ other updates in Update Managar today and when I hit the install updates button I had to fumble for the cancel button because it went to the dist-upgrade screen.  How can I tell what packages will trigger the Ubuntu upgrade so I can freeze them?

---

### Post by 3Miro on 2011-04-28
System -> Admin -> Update Manager -> Settings (lower left corner), then "Show new distribution release", you can set this one to "never".

10.10 will be supported for another 12 months so you can keep using it until the next LTS release in 12.04.

---

### Post by pctx on 2011-04-28
For work, I've got 10.10 right where I want it.
Home, I'm upgrading.  Just got my work machine nice and stable and I don't want to nix it.

Be interesting to see what other people do as well.

---

### Post by jlbrewer on 2011-04-28
> **3Miro said:**
> System -> Admin -> Update Manager -> Settings (lower left corner), then "Show new distribution release", you can set this one to "never".


Ok, done, but trying to run all the offered updates still presents me with the distribution upgrade confirmation screen.  A lot of the updates are KDE (installed as Ubuntu, installed kubuntu separately as an option for people) so I wonder if that's what's triggering it.

---

### Post by 3Miro on 2011-04-29
I don't know. You may try to log into KDE and check the System Settings. They may have other options under the Update Manager section.

---

### Post by ivanovnegro on 2011-04-29
> **3Miro said:**
> I don't know. You may try to log into KDE and check the System Settings. They may have other options under the Update Manager section.

Under KDE its the same thing, choose "never" or "LTS" as upgrade options from KPackageKit.

---

