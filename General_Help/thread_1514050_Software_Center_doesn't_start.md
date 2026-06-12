---
title: "Software Center doesn't start"
date: 2010-06-20
forum: General Help
---

### Post by sheerun on 2010-06-20
When I start software-center 2.1.3 on Ubuntu 10.04 LTS
 following message shows in terminal and utility crashes:

```
WARNING:root:No styling hints for Shiki-Dust were found... using Human hints.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 83, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, enable_lp_integration=options.enable_lp)
  File "/usr/share/software-center/softwarecenter/app.py", line 284, in __init__
    self.restore_state()
  File "/usr/share/software-center/softwarecenter/app.py", line 705, in restore_state
    self.available_pane.cat_view.carosel.show_carosel(False)
  File "/usr/share/software-center/softwarecenter/view/catview_gtk.py", line 735, in show_carosel
    btn = self.show_hide_btn
AttributeError: 'FeaturedView' object has no attribute 'show_hide_btn'

```

Anybody? :(

---

### Post by Rubi1200 on 2010-06-20
Maybe try going to Synaptic and searching for software-center then re-install and see if that helps.

Other than that, when did this occur; after an upgrade, recently installed software etc.?

---

### Post by sheerun on 2010-06-20
Reinstall didn't help.

I think it was after some upgrade. Is there any way to reverse it? Approximately two days ago everything was fine.

---

### Post by Rubi1200 on 2010-06-20
Not sure what to tell you about this. Maybe submit a bug report or look if others have had a similar problem.
Meantime, you can still install software via Synaptic right?

---

### Post by sheerun on 2010-06-20
Google's keeps quiet. Apt-get and synaptic are all right. 

Something's wrong with software-center. I've checked logs and it was updated yesterday:

```
2010-06-19 00:39:40 upgrade software-center 2.1.2.1 2.1.3
2010-06-19 00:39:40 status half-configured software-center 2.1.2.1
2010-06-19 00:39:41 status unpacked software-center 2.1.2.1
2010-06-19 00:39:43 status half-installed software-center 2.1.2.1
2010-06-19 00:39:45 status unpacked software-center 2.1.3
```

---

### Post by Rubi1200 on 2010-06-20
> **sheerun said:**
> Google's keeps quiet. Apt-get and synaptic are all right. 

Something's wrong with software-center. I've checked logs and it was updated yesterday:

```
2010-06-19 00:39:40 upgrade software-center 2.1.2.1 2.1.3
2010-06-19 00:39:40 status half-configured software-center 2.1.2.1
2010-06-19 00:39:41 status unpacked software-center 2.1.2.1
2010-06-19 00:39:43 status half-installed software-center 2.1.2.1
2010-06-19 00:39:45 status unpacked software-center 2.1.3
```

It looks as if it got stuck along the way and the upgrade did not complete. 

I checked Launchpad but didn't find anything there.

Did you try reinstalling the latest version or the previous one?

Maybe you could try again and install version 2.1.2.1 (assuming this was the version that you said worked for you) then lock it. Just a thought.

---

### Post by sheerun on 2010-06-20
OK. I've installed 2.0.5 and Software Center's working now.

Thank You for interest

---

