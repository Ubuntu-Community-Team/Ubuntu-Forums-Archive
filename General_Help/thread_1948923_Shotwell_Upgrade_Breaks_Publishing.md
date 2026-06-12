---
title: "Shotwell Upgrade Breaks Publishing"
date: 2012-03-29
forum: General Help
---

### Post by mrkeef on 2012-03-29
I just upgraded to shotwell 0.12 from the ppa, lured by the promise of publishing to flickr being fixed.

Now I cannot publish to any service other than piwigo. The option are just not there.

Have I got a broken installation or is there a problem in shotwell?

Under /usr/lib/shotwell/plugins/builtin I have the following files (excluding the .png icons):

[INDENT]piwigo_authentication_pane.glade
piwigo_publishing_options_pane.glade
shotwell-data-imports.so
shotwell-publishing.so
shotwell-publishing-extras.so
shotwell-transitions.so
yandex_publish_model.glade

[/INDENT]
Using Ubuntu 11.10

Thanks

Keith

---

### Post by eric-yorba on 2012-03-29
Two things:

1. Make sure the publishing options are enabled in the plugin preferences.
2. We're going to have 0.12.1 out very, very soon.  If you've added the PPA it will update automatically.  This fixes a number of packaging issues which might resolve this.

---

### Post by mrkeef on 2012-03-29
I just upgraded to 0.12.1 but the problem remains.

The only publishing options given in the Preferences- Plugins menu are for Piwigo and Yandex-Fotki

Keith

---

### Post by matala on 2012-03-31
I have the same problem after updated to 0.12.1 :confused:

---

### Post by eric-yorba on 2012-04-02
Did you update from the PPA?  I believe there was a packaging error.

If you did, try doing an update.  The new package should resolve the issue.

---

### Post by mrkeef on 2012-04-02
> **eric-yorba said:**
> Did you update from the PPA?  I believe there was a packaging error.



Yes, I was using the PPA. I updates, and it does work now.

Thanks for fixing it.

There is one issue and that is that the first time I tried to upload to flickr, shotwell crashed- just disappeared. I restarted and it worked fine after that. It was the first time I tried to upload to any service so whether it is related specifically to flickr or to uploading generally I can't tell you.

Cheers

Keith

---

