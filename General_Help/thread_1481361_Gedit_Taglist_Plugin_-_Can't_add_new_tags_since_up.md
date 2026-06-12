---
title: "Gedit Taglist Plugin - Can't add new tags since upgraded to Lucid"
date: 2010-05-12
forum: General Help
---

### Post by Techjacker on 2010-05-12
I'm trying to install extra tags into the taglist plugin for gedit.

Since upgrading to Lucid I've been unable to make this work.

Has anyone else experienced this problem?

I've tried putting them in both the following locations without joy:
/usr/share/gedit-2/taglist
~/.gnome2/gedit/taglist
/usr/share/gedit-2/plugins/taglist

I've also tried putting the tags in there in both compressed and non-compressed format:
css.tags.gz
css.tags

Any ideas on what I'm doing wrong?

---

### Post by Techjacker on 2010-05-12
I figured out the solution after some more trial and error.

1. you need to deactivate the taglist plugin after copied in new tags
2. restart gedit
3. then reactivate the taglist plugin and they should all show up in the sidepanel

not sure if any of the compression stuff I did was necessary or which is the actual directory it's picking up the tags from in the end but hey who cares?!

can't believe I wasted so much time on a problem that was so simple to fix!

---

### Post by blaz_boy on 2010-09-01
i want to add that , taglist should be copied to :
> ~/.gnome2/gedit/taglist

the **/user/share directory** not working

---

