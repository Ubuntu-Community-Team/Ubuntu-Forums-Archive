---
title: "gconf-editor thumbnail_cache values"
date: 2010-05-12
forum: General Help
---

### Post by sunshinecorp on 2010-05-12
> The thumbnail cache is cleared if there is an excess of the maximum cache age or the maximum cache size; This can be configured with gconf-editor in:

    * /desktop/gnome/thumbnail_cache/max_size (maximum size cache)
    * /desktop/gnome/thumbnail_cache/max_age (maximum age of a thumbnail)

Does anyone know what will happen if I choose to set these to values "0" or "-1". It is possible to do so with *Ubuntu Tweak* but I haven't found any documentation on those values. Which one do I use to completely disable caching?

Thank you in advance!

**SOLVED:**

I found the answer after some rigorous research, and decided to post it to help others who have the same question.

Value "0" means that the cache will be cleared upon logout.
Value "-1" means that the cache will never be cleared.

---

