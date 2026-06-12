---
title: "firefox doesn't render pages properly due to font problems"
date: 2011-02-12
forum: General Help
---

### Post by robertbub on 2011-02-12
It seems that I have been running Firefox unbeknownst to me with a broken configuration.  It seems that if I enable the > Allow pages to choose their own fonts, instead of my selections abovein Edit->Preferences->Content->Fonts&Colors->Advanced, pages will no longer be render properly -- they are mostly blank.

When running on the command line, I notice that I get errors from Pango (whatever that is) and think there may be a connection.  I pasted the errors below.

I tried doing **sudo aptitude reinstall libpango-perl libpango1.0-0 libpango1.0-common libpangomm-1.4-1** but it didn't fix the problems.  (I haven't yet tried uninstalling pango since it looks like it removes some crucial components.)

I also tried **sudo dpkg-reconfigure fontconfig** and it didn't help.

I'm guessing that the fonts cannot be scaled.

This otherwise wouldn't be an issue, but it seems that some Firefox addons forcibly ignore the configured fonts and those pop-up windows are mostly blank/empty and therefore useless.

Does anyone know how this problem could be fixed?

```
(firefox-bin:6964): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 22.6669921875', text='Web Images Videos'

(firefox-bin:6964): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 22.6669921875', text='Maps'

(firefox-bin:6964): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 24', text=' '

(firefox-bin:6964): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 27.599609375', text='Search Maps'

```

---

### Post by robertbub on 2011-02-12
OK, I fixed it.

I realized that I had a bunch of symbolic links in my $HOME/.fonts directory to /usr/share/fonts/truetype/msttcorefonts .  That directory was virtually empty except a README which essentially said to **sudo apt-get install --reinstall ttf-mscorefonts-installer**.

This cranked a bit and when it was all done, everything now works!

---

### Post by Habitual on 2011-02-13
+1 for fixing your own stuff. :)

---

