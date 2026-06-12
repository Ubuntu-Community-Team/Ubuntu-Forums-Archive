---
title: "Hydrogen &amp; LadspaFX- setting the environment variable directory?"
date: 2006-05-28
forum: General Help
---

### Post by Cordate on 2006-05-28
I've got Hydrogen installed and working, and I went to plugin.org.uk and installed a pack of fx plugins. It looks like they were installed in /usr/local/lib/ladspa

When I run Hydrogen it's not finding them. It looks like I need to set something up for it so that it knows to use that directory instead of the one that it's currently using:

```
Using data path: /usr/share/hydrogen/data
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] directory /usr/lib/ladspa not found
```

So my question is: how do I do that? 8)

I feel like I'm 90% done, it's just this one part that I'm drawing a blank on. Thanks for any help!

Edit: there's a mention of this on this page : [http://www.hydrogen-music.org/forum/index.php?action=show_thread&thread=111&fid=0&page=1](http://www.hydrogen-music.org/forum/index.php?action=show_thread&thread=111&fid=0&page=1) but I'm still not sure how (where?) I would set LADSPA_PATH...

---

### Post by Cordate on 2006-05-29
Ok, I think I got it after some browsing and guessing and a reboot. I'll post the info here in case anyone else ends up having the same question:

I edited the environment file
```
sudo gedit //etc/environment
```
and added a line
```
LADSPA_PATH=/usr/local/lib/ladspa
```
and retried Hydrogen, but it looked like it still wasn't finding it. But this morning it's there, and I think having rebooted the computer helped set this path where Hydrogen could find it. Now I'm off to play with all these funky FX! :)

---

