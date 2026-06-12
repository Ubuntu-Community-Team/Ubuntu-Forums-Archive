---
title: "Recent Applications Not Being Recorded In Unity Home Lens"
date: 2012-09-03
forum: General Help
---

### Post by andygmorris on 2012-09-03
Rgarding: Ubuntu 12.04.1 LTS (64-bit)

Hi all.

When I open applications from Unity inside the Applications lens, or from the sidebar, the applications are no longer being shown in the "Recent Apps" of the Home lens.

By following previous posts from November and April, I have already tried :-

- remove the files in ~/.local/share/zeitgeist/
(the above forces a rebuild of zeitgeist on next login)

- remove the file ~/.local/share/recently-used.xbel
(the above removes ALL recently open files history)

When opening the text editor, a calculator, a spreadsheet etc, nothing is being recorded in "Recent Apps".

"Recent Files" are being recorded in the Home lens ok.
It's just "Recent Apps" that are not.

Does anyone have any ideas?

---

### Post by andygmorris on 2012-09-04
A 'solution', or should I say 'an understanding' has been found!

As commented on in this post :-
[http://ubuntuforums.org/showthread.php?p=12216321](http://ubuntuforums.org/showthread.php?p=12216321)

It seems that applications will not be shown in the Recent Apps section in the Dash Home lens or in the Recently Used section in Dash Applications lens when the application is :-

1) manually pinned to the sidebar, or
2) actively open/in-use (therefore in the sidebar!)

So now we know!

This explains as the more I used Unity, the more apps I pinned to the sidebar, and effectively my Recent Apps 'looked like' they were disappearing.

Hope the info helps someone else.

---

