---
title: "Question about Firefox 8 and plugin locations"
date: 2011-12-09
forum: General Help
---

### Post by tomdkat on 2011-12-09
I'm running Firefox 8 on Ubuntu 11.10 (64-bit) and I want to know the installation path of the Flash plugin.  When I look at the installed plugins from within Firefox itself, I can see the file names of the plugins but I can't see the locations of the files, as I used to in previous versions of Firefox.

I have a problem where Flash video doesn't play in Firefox 8 but it plays in Opera 11.60 and I want to make sure they're using the same plugin.

How can I determine the location of any given plugin that Firefox is actually loading?

Thanks!

Peace...

---

### Post by Bobhuber on 2011-12-09
> **tomdkat said:**
> I'm running Firefox 8 on Ubuntu 11.10 (64-bit) and I want to know the installation path of the Flash plugin.  When I look at the installed plugins from within Firefox itself, I can see the file names of the plugins but I can't see the locations of the files, as I used to in previous versions of Firefox.

I have a problem where Flash video doesn't play in Firefox 8 but it plays in Opera 11.60 and I want to make sure they're using the same plugin.

How can I determine the location of any given plugin that Firefox is actually loading?

Thanks!

Peace...

about:config

plugin.expose_full_path     >        true

---

### Post by tomdkat on 2011-12-10
Thanks!  Apparently, I had that setting already set to true but now the full path is showing.  Weird.

Anyway, thanks again!

Peace...

---

