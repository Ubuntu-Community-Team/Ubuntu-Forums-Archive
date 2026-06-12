---
title: "Phonetic Russian input in Kubuntu 10.04"
date: 2010-08-12
forum: General Help
---

### Post by ShadowWraith on 2010-08-12
In earlier versions of (K)ubuntu, I have used SCIM and the Yawerty input method to input Russian with a phonetic Latin keyboard.
SCIM does not seem to work with Kubuntu 10.04, and UIM does not have (as far as I can tell from searching the repositories) Russian input.

The Russian keyboard layout installable in Kubuntu is in the Russian version of the layout, rather than a phonetic Latin layout; I am not familiar with the normal Russian layout and I do not have stickers to stick on the keys to guide myself in using that layout.

Does anyone have a solution?

---

### Post by simosx on 2010-08-12
In Ubuntu 10.04 you use IBus instead of SCIM. So, remove anything you installed relating to SCIM and configure IBus. Hopefully there should be no left-over files that may mess your setup.

SCIM layouts work with IBus; the layouts should be already installed in Ubuntu.

---

### Post by ShadowWraith on 2010-08-13
Ibus doesn't play nice with KDE; it refuses to acknowledge input windows and doesn't detect my installed SCIM input tables for Russian.

I installed the package keyboards-rg and it added a phonetic russian layout to the KDE keyboard layouts, so guess the problem is solved, though I'd rather have all my inputs accessible from the toolbar rather than have to use UIM for Japanese and the kde layout widget for the others.

---

