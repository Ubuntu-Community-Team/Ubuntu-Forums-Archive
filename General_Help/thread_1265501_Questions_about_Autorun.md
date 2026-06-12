---
title: "Questions about Autorun"
date: 2009-09-13
forum: General Help
---

### Post by risingsun on 2009-09-13
Hi,

I noticed that while intrepid used to have autorun prompts for CD's (even windows targeted ones) I've not yet seen any such prompt under Jaunty. I only really have windows CD's to test with so I might presume that autorun may well have been disabled for those completely, but is this prompt still in Jaunty and set to use by default?

As a follow on from that, how can you view and/or configure the autorun settings, and what are Jaunty's default settings?

Many thanks.

---

### Post by Tamlynmac on 2009-09-13
The autorun check box is located here:

system tools/configuration editor/apps/nautilus/preferences/media_autorun_never

Other autorun setting are also listed there. For example, "media_autorun_x_content_start_app" should list the preferred content type to be autorun - that were select in "filebrowser/edit/preferences/media tab".

"media_autorun_x_content_ignored" is a listing of content to be ignored by autorun.

If you lift click once one each line it will give you a description of the key at the bottom.

One last thought (I've never tried it) In "filebrowser/edit/preferences/media tab" uncheck the box "Browse media when inserted" (media_automount_open). Which would then never open a folder when media is automounted. I believe this would only apply to media that hasn't been pre-selected in the media tab.

Good Luck and hope this is what your looking for.

---

